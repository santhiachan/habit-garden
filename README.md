<div align="center">

# 🌱 Habit Garden · 习惯小花园
网址：https://santhiachan.github.io/habit-garden/Habit_Garden.html 
也可以架设到自己的服务器上。

**用养植物的方式养成好习惯**

*A cozy habit tracker that grows a plant as you grow yourself.*

<br>

<img src="https://img.shields.io/badge/vanilla-HTML%2FCSS%2FJS-f3d388?style=flat-square" alt="Vanilla HTML/CSS/JS">
<img src="https://img.shields.io/badge/backend-Firebase-f2a78d?style=flat-square&logo=firebase&logoColor=white" alt="Firebase">
<img src="https://img.shields.io/badge/file-single%20HTML-7a9b6e?style=flat-square" alt="Single HTML File">
<img src="https://img.shields.io/badge/i18n-中文%20%2F%20English-c4b5d9?style=flat-square" alt="Bilingual">

<br><br>

> 🫛 每完成一项习惯，你的小植物就长大一点。
> 不急不赶，慢慢来。

<br>

<!-- 如果你有截图，取消下面这行的注释并替换链接 -->
<!-- <img src="./screenshots/hero.png" width="720" alt="Habit Garden 截图"> -->

</div>

---

## ✨ 这是什么？

**Habit Garden** 是一个温暖、可爱的网页打卡应用。它把枯燥的习惯养成变成了一场小小的种植游戏 —— 你做任务获得经验值，经验值让你的植物从一颗种子慢慢长成一棵开花结果的大树。

整个应用是**一个 HTML 文件**，没有构建工具、没有框架依赖，打开即用。数据通过 Firebase 同步到云端，支持跨设备登录。

---

## 🌿 功能一览

### 🪴 养成系宠物

打开盲盒获得一颗随机种子 —— 毛豆、玫瑰、番茄、仙人掌、龟背竹，五种植物随机掉落。你的植物会随经验值成长，经历 **6 个阶段**：

> 小种子 → 萌芽期 → 小芽豆 → 青青豆 → 圆滚豆 → 星辰豆

成熟后还会结出果实，植物的表情会随你的打卡状态变化 —— 开心、平静或沮丧。

### 📋 灵活的任务系统

- **每日任务**：每天重置，适合日常养成（读书、练琴、早睡……）
- **一次性任务**：做完即消失，适合阶段性挑战
- **半完成机制**：先「启动」拿一半奖励，降低开始的阻力；完成后再拿另一半
- **四级难度**：🌱小事 · 🌿一般 · 🌳挑战 · 🌲大事，奖励从 5xp 到 60xp

### 🏅 五维能力值

每个任务归属一个维度，完成后累计对应属性：

| 💼 事业 | 💖 魅力 | 💰 财富 | 📚 智慧 | 🌿 健康 |
|:------:|:------:|:------:|:------:|:------:|
| Career | Charm | Wealth | Wisdom | Health |

### 🎁 许愿商店

用打卡赚的 ⭐ 星星兑换奖励 —— 这些奖励是你平时「偷懒」会做或「犹豫太久」不敢做的事。兑换后请无罪恶感地享受。支持自定义奖励和限购次数。

### 🃏 卡片收藏册

完成任务有机率掉落植物卡片，分为四种稀有度：

| 普通 | 稀有 | 史诗 | 传说 |
|:---:|:---:|:---:|:---:|
| Common | Rare | Epic | Legendary |

五大维度各有独立卡池，传说卡极为稀有。

### ⏱ 专注模式

内置番茄钟，「坐下 5 分钟就能开始」。支持 5 / 15 / 25 / 45 分钟时长，启动即奖励 —— 因为启动比完成更重要。

### 🌙 心情与记录

- **每日心情**：选择心情关键词标记当天状态，支持自定义标签
- **一句话日记**：随手写下今天的一个小发现或小感受
- **心情统计**：按周/月/全部查看心情趋势
- **睡眠计划**：每晚记录打算几点睡

### 🫂 低落时的安慰

当你点击「今天有点不行」，不会得到说教 —— 只有一句温柔的话和一个拥抱按钮。

---

## ☁️ 云端同步

通过 Firebase Authentication + Firestore 实现：

- **Google 账号** 或 **邮箱密码** 登录
- 数据实时同步到云端，跨设备可用
- 带同步状态指示（🟢 正常 · 🟡 同步中 · 🔴 出错）
- 点击用户徽章可手动强制刷新
- 离线时自动回退到 localStorage，不会卡死

---

## 🚀 部署方式

### 最简单：直接打开

```
双击 Habit_Garden_firebase_v2.html → 浏览器打开 → 完事
```

> ⚠️ `file://` 协议下 Google 登录不可用，但邮箱注册/登录可以正常使用。

### 推荐：部署到 GitHub Pages / Netlify / Vercel

1. Fork 这个仓库
2. 在 [Firebase Console](https://console.firebase.google.com/) 打开你的项目
3. **Authentication → Settings → Authorized domains** 中添加你的域名
4. **Firestore → Rules** 中设置安全规则：

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

5. 推送代码，访问你的域名即可

### 想用自己的 Firebase 项目？

在 HTML 文件底部找到 `firebaseConfig` 对象，替换成你自己的配置：

```javascript
const firebaseConfig = {
  apiKey: "你的-api-key",
  authDomain: "你的项目.firebaseapp.com",
  projectId: "你的项目",
  // ...
};
```

---

## 🛠 技术栈

| 层 | 技术 |
|---|------|
| 前端 | 纯 HTML + CSS + Vanilla JS（单文件，无框架） |
| 字体 | Google Fonts — Caveat · Fraunces · LXGW WenKai TC |
| 认证 | Firebase Authentication（Google + Email/Password） |
| 数据库 | Cloud Firestore（实时同步 + 离线 localStorage 备份） |
| 部署 | 任何静态托管（GitHub Pages / Netlify / Vercel / 直接打开） |
| 国际化 | 中文 / English 双语切换 |

---

## 📁 项目结构

```
.
└── Habit_Garden_firebase_v2.html   ← 就这一个文件，所有代码都在里面
```

是的，真的就一个文件。

---

## 🎨 设计理念

- **温暖而不幼稚** —— 奶油色调 + 手写字体 + 植物主题，像一本手帐
- **鼓励而不说教** —— 「启动比完成更重要」，先迈出 5 分钟就给奖励
- **游戏化但不上瘾** —— 经验值、卡片、盲盒都是锦上添花，核心还是帮你养成习惯
- **离线优先** —— 断网也能用，联网后静默同步

---

## 📜 License

MIT

---

<div align="center">

*一棵植物不会一天长大，一个习惯也是。*

*A plant doesn't grow in a day — and neither does a habit.*

🌱

</div>
