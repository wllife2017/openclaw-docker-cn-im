# OpenClaw-Docker-CN-IM

> 面向中国 IM 场景的 OpenClaw Docker 整合镜像，预装飞书、钉钉、QQ 机器人、企业微信等常用插件，适合快速搭建统一的 AI 机器人网关。

> 🚀 **推荐搭配**：OpenClaw 功能强大但 Token 消耗较大，推荐配合 [AIClient-2-API](https://github.com/justlovemaki/AIClient-2-API) 项目使用，将各大 AI 客户端转换为标准 API 接口，实现无限 Token 调用，彻底解决 Token 焦虑！本项目已支持 OpenAI 和 Claude 两种协议，可直接对接 AIClient-2-API 服务。

<table align="center">
  <thead>
    <tr>
      <th align="center">镜像下载量超100k</th>
      <th align="center">好用给个赞助吧</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center" valign="middle">
        <img src="https://sweet-union-c569.justlikemaki.workers.dev/justlikemaki/openclaw-docker-cn-im?layout=compact&theme=github" alt="openclaw-docker-cn-im" style="width: 100%; max-width: 520px; height: 320px; object-fit: contain;" />
      </td>
      <td align="center" valign="middle">
        <img src="sponsor.png" alt="微信赞赏码" style="width: 100%; max-width: 260px; height: 320px; object-fit: cover; object-position: center;" />
      </td>
    </tr>
  </tbody>
</table>

## 项目简介

本项目提供一个开箱即用的 OpenClaw Docker 镜像，并围绕国内 IM 场景做了整合与增强：

- 预装多种中国 IM 平台插件
- 支持通过环境变量自动生成配置
- 支持多 Provider / 多模型配置
- 支持多账号飞书、钉钉、企业微信、QQ Bot 配置
- 支持多 Agent 与多机器人绑定路由示例
- 集成 OpenCode AI、Playwright、FFmpeg、中文 TTS
- 提供独立工具容器，用于执行飞书官方插件安装等一次性操作

项目地址：<https://github.com/justlovemaki/OpenClaw-Docker-CN-IM>

## 文档导航

### 新手入口

1. 先阅读 [`docs/quick-start.md`](docs/quick-start.md)
2. 然后按需查看 [`docs/configuration.md`](docs/configuration.md)
3. 需要接入具体平台时，优先查看插件提供方文档：
   - 飞书官方团队插件：<https://github.com/larksuite/openclaw-lark>
   - 飞书旧版内置插件示例：<https://github.com/openclaw/openclaw/blob/main/docs/channels/feishu.md>
   - 钉钉插件：<https://github.com/soimy/openclaw-channel-dingtalk>
   - QQ 机器人插件：<https://github.com/sliverp/qqbot>
   - 企业微信插件：<https://github.com/sunnoy/openclaw-plugin-wecom>
4. 遇到问题时查看 [`docs/faq.md`](docs/faq.md)

### 文档索引

| 文档 | 内容 |
| --- | --- |
| [`README.md`](README.md) | 项目总览、版本更新、快速入口 |
| [`docs/quick-start.md`](docs/quick-start.md) | 快速部署、升级、日志、进入容器 |
| [`docs/configuration.md`](docs/configuration.md) | 模型、Gateway、工作空间、Compose 与环境变量说明 |
| [`docs/aiclient-2-api.md`](docs/aiclient-2-api.md) | 对接 AIClient-2-API 的推荐方式 |
| [`docs/advanced.md`](docs/advanced.md) | Docker 命令运行、数据持久化、自定义配置 |
| [`docs/faq.md`](docs/faq.md) | 常见问题与故障排查 |
| [`docs/developer-notes.md`](docs/developer-notes.md) | 镜像构建、文件说明、初始化脚本说明 |
| 外部插件文档 | 飞书：<https://github.com/larksuite/openclaw-lark> / <https://github.com/openclaw/openclaw/blob/main/docs/channels/feishu.md>；钉钉：<https://github.com/soimy/openclaw-channel-dingtalk>；QQ：<https://github.com/sliverp/qqbot>；企业微信：<https://github.com/sunnoy/openclaw-plugin-wecom> |

---

## 核心特性

- 🚀 开箱即用：镜像内已集成常见中国 IM 插件
- 🔧 环境变量驱动：通过 [`.env.example`](.env.example) 快速生成配置
- 🐳 Docker 部署友好：默认提供 [`docker-compose.yml`](docker-compose.yml)
- 📦 数据持久化：支持挂载 OpenClaw 数据目录
- 🤖 多模型支持：支持 OpenAI 协议与 Claude 协议
- 🧩 多账号能力：飞书、钉钉、企业微信、QQ Bot 均支持更复杂的账号组织方式
- 🧭 多 Agent 路由：支持按机器人账号将消息路由到不同 OpenClaw Agent
- 🛠️ 工具增强：集成 OpenCode AI、Playwright、FFmpeg、中文 TTS

## 支持的平台与工具

### IM 平台

- ✅ 飞书官方团队插件
- ✅ 飞书旧版内置插件
- ✅ 钉钉
- ✅ QQ 机器人
- ✅ 企业微信

### 集成工具

- ✅ OpenCode AI
- ✅ Playwright
- ✅ 中文 TTS
- ✅ FFmpeg
- ✅ 飞书官方 OAPI 工具集

## Docker 镜像

Docker Hub：<https://hub.docker.com/r/justlikemaki/openclaw-docker-cn-im>

```bash
docker pull justlikemaki/openclaw-docker-cn-im:latest
```

---

## 仓库中的关键文件

| 文件 | 说明 |
| --- | --- |
| [`docker-compose.yml`](docker-compose.yml) | 默认部署编排 |
| [`.env.example`](.env.example) | 环境变量模板 |
| [`Dockerfile`](Dockerfile) | 镜像构建定义 |
| [`init.sh`](init.sh) | 容器启动初始化脚本 |
| [`openclaw.json.example`](openclaw.json.example) | 默认配置结构示例 |

## 使用建议

- 生产或长期维护场景，建议直接克隆仓库而不是只单独下载 [`docker-compose.yml`](docker-compose.yml) 和 [`.env.example`](.env.example)
- 每次升级前，先同步 [`README.md`](README.md)、[`docker-compose.yml`](docker-compose.yml)、[`.env.example`](.env.example) 与新增文档
- 如果你手动维护 [`openclaw.json`](openclaw.json.example)，建议同时关注 [`openclaw.json.example`](openclaw.json.example) 的结构变化

## Star History

如果项目对你有帮助，欢迎点一个 Star。

[![Star History Chart](https://api.star-history.com/svg?repos=justlovemaki/OpenClaw-Docker-CN-IM&type=Date)](https://star-history.com/#justlovemaki/OpenClaw-Docker-CN-IM&Date)

## 许可证

本项目基于 OpenClaw 构建，遵循 GNU General Public License v3.0 (GPL-3.0) 许可证，详见 [`LICENSE`](LICENSE)。
