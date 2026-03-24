# 📋 DANH SÁCH FILE ĐÃ TẠO

## Cây thư mục — copy vào project Next.js hiện tại

```
project-root/
│
├── app/
│   └── dashboard/
│       └── page.tsx                     ✅ Server wrapper → import DashboardClient
│
├── components/
│   │
│   ├── dashboard/
│   │   ├── DashboardClient.tsx          ✅ ⭐ MAIN — login screen + 4 trang + topbar
│   │   ├── DonutChart.tsx               ✅ SVG donut chart tiến độ (dễ/trung/khó)
│   │   ├── Heatmap.tsx                  ✅ GitHub-style heatmap 12 tuần
│   │   ├── ActivityBarChart.tsx         ✅ Recharts bar chart số bài 7 ngày
│   │   ├── SkillRadarChart.tsx          ✅ Recharts radar chart 6 kỹ năng
│   │   └── ProblemsTable.tsx            ✅ Table bài đã giải + search real-time
│   │
│   └── practice/
│       └── SolvePage.tsx                ✅ ⭐ Upload ảnh→AI→Editor→Judge→Hint
│
└── lib/
    ├── types.ts                         ✅ Tất cả TypeScript interfaces
    ├── constants.ts                     ✅ Mock data, màu sắc, code templates
    ├── user.ts                          ✅ User class với private fields (#)
    ├── ai.ts                            ✅ Anthropic API helpers
    └── utils.ts                         ✅ cn(), formatDate(), percent()
```

---

## 📝 Chi tiết từng file

| File | Mục đích | Ghi chú |
|------|----------|---------|
| `lib/types.ts` | TypeScript interfaces | Dùng xuyên suốt project |
| `lib/constants.ts` | Mock data + config | Thay bằng API sau |
| `lib/user.ts` | User class (#private) | Mọi thứ = 0 khi chưa nhập tên |
| `lib/ai.ts` | Anthropic API | Cần `ANTHROPIC_API_KEY` trong `.env.local` |
| `lib/utils.ts` | Helpers | `cn()` cần cho shadcn/ui |
| `components/dashboard/DashboardClient.tsx` | ⭐ Component chính | `"use client"`, chứa toàn bộ state |
| `components/dashboard/DonutChart.tsx` | Vòng tròn tiến độ | SVG thuần, không cần lib |
| `components/dashboard/Heatmap.tsx` | Lịch sử nộp bài | 84 ngày, 5 cấp màu |
| `components/dashboard/ActivityBarChart.tsx` | Biểu đồ 7 ngày | Dùng `recharts` (đã có trong package.json) |
| `components/dashboard/SkillRadarChart.tsx` | Radar kỹ năng | Dùng `recharts` |
| `components/dashboard/ProblemsTable.tsx` | Bảng bài đã giải | Dùng shadcn/ui `Table` |
| `components/practice/SolvePage.tsx` | ⭐ Trang giải bài | Upload→AI→Code→Judge |
| `app/dashboard/page.tsx` | Next.js page | Server Component wrapper |

---

## 🚀 Cách dùng

### 1. Copy file vào project
```bash
# Copy từng folder vào project root
cp -r lib/ your-project/
cp -r components/dashboard/ your-project/components/dashboard/
cp -r components/practice/  your-project/components/practice/
cp app/dashboard/page.tsx   your-project/app/dashboard/page.tsx
```

### 2. Thêm API key
```bash
# .env.local
ANTHROPIC_API_KEY=sk-ant-api03-...
```

### 3. Chạy
```bash
pnpm dev
# Mở http://localhost:3000/dashboard
```

---

## 📦 Dependencies đã có sẵn (không cần cài thêm)

| Package | Dùng trong |
|---------|-----------|
| `recharts` | ActivityBarChart, SkillRadarChart |
| `lucide-react` | Icons |
| shadcn/ui (`Badge`, `Button`, `Input`, `Table`) | Tất cả components |
| `tailwindcss` | Styling |

---

## 🔌 Kết nối Backend sau

- **Mock data** → `lib/constants.ts` → thay bằng `fetch()`
- **User data** → `lib/user.ts#loadDefaultData()` → fetch từ DB
- **AI** → `lib/ai.ts` → đã sẵn sàng, chỉ cần API key
