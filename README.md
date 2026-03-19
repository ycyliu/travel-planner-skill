# Travel Planner Skill

**旅行路线规划与精美攻略生成** — 一个为 [WorkBuddy](https://www.codebuddy.cn/docs/workbuddy/Overview) / CodeBuddy 设计的 AI Agent Skill。

## 功能

- 根据用户需求（目的地、天数、偏好），自动研究目的地信息并生成精美的 HTML 旅行攻略
- **小红书优先**：优先从小红书搜索真实用户反馈（价格、踩坑、拍照机位），再用公开搜索补充验证
- **一键生成**：确认需求后全自动执行——信息研究 → 路线规划 → HTML 页面生成 → 预览
- **预算预估**：自动计算三档预算（经济/舒适/豪华），含机票、酒店、门票、餐饮等明细
- **响应式设计**：生成的 HTML 页面适配桌面和移动端，支持直接打印为 PDF

## 工作流

```
Phase 1: 需求确认（唯一需要用户交互的步骤）
    ↓
Phase 2: 信息研究（小红书深度研究 + 公开网络搜索）
    ↓
Phase 3: 路线规划（分段、每日安排、主题命名）
    ↓
Phase 4: HTML 攻略页面生成 + 预览
```

### 小红书集成

本 Skill 的核心差异化能力是**小红书数据优先**：

- 搜索策略覆盖：攻略、避坑、费用、住宿、美食、拍照等多维度
- 深挖高质量笔记的正文 + 评论区（评论区往往有更新的价格和纠错信息）
- 内置故障恢复：登录状态检查 → 自动扫码 → 超时重试 → 明确的跳过条件

> 需要配合 [xiaohongshu-mcp](https://github.com/jinjunzh/xiaohongshu-mcp) 使用

## 安装

### WorkBuddy / CodeBuddy

将此仓库克隆到 skills 目录：

```bash
# WorkBuddy
git clone https://github.com/ycyliu/travel-planner-skill.git ~/.workbuddy/skills/travel-planner

# 或 CodeBuddy
git clone https://github.com/ycyliu/travel-planner-skill.git ~/.codebuddy/skills/travel-planner
```

### 触发词

安装后，以下关键词会自动触发本 Skill：

> 去哪玩、旅行攻略、旅游路线、出行规划、自驾游、周末去哪、假期规划、行程安排、旅行计划、景点推荐、几日游、路线规划

## 生成效果

攻略页面包含以下板块：

| 板块 | 说明 |
|------|------|
| Hero 区域 | 目的地大标题 + 日期/里程/分段/重点提醒 |
| 路线总览 | 线性路线图 + 每段卡片（特色、亮点） |
| 每日行程 | 时间线式安排 + 侧边栏亮点/提醒 |
| 预约与行前准备 | 门票预约表 + 交通方式 + 预约渠道 |
| 实用建议 | 住宿/美食/餐饮推荐 |
| 预算预估 | 费用明细表 + 三档总预算 + 省钱贴士 |
| 出发前检查 | 注意事项 + 携带清单 |

### 设计风格

- 暖色调（深金棕 + 暖金 + 奶白背景）
- 圆角卡片、柔和阴影
- 全内联 CSS，不依赖任何外部资源
- 打印友好，可直接导出 PDF

## 文件结构

```
travel-planner/
├── SKILL.md                       # Skill 定义（工作流 + 设计规范）
├── references/
│   └── template-example.html      # HTML 模板（带占位符）
├── assets/                        # 静态资源（预留）
├── scripts/                       # 脚本工具（预留）
└── README.md
```

## 依赖

- **必需**：WorkBuddy / CodeBuddy（或兼容的 AI Agent 环境）
- **推荐**：[xiaohongshu-mcp](https://github.com/jinjunzh/xiaohongshu-mcp)（小红书数据源）
- **无外部依赖**：生成的 HTML 页面完全自包含

## 许可

MIT License
