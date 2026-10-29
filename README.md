# ST-Bridge Context

SillyTavern / TauriTavern 前端扩展，把酒馆插件的请求接到本机 **ST-bridge** 的 DSH 持久会话。

## 功能

- 按酒馆聊天自动注入或改写 `dsh_session`，让每个聊天对应独立的 DSH 会话；
- 固定预设 / 固定规则与动态资料分离；
- 清理发送副本里的 `<bbi_image>` 等生图占位块；
- 世界书排除、条目名过滤、绿灯筛选（按请求范围配置）；
- 桥接收件回执、本次发送预览、上下文审计；
- 只改发送副本，不修改酒馆原文。

## 依赖

需要先安装并运行 DSH 插件：

https://github.com/wuhehen176/ST-bridge

桥接默认地址：

```text
http://127.0.0.1:43121/v1
```

## 安装

### SillyTavern

扩展 → 安装扩展 → 填入本仓库地址：

```text
https://github.com/wuhehen176/ST-bridge-tavern
```

安装后刷新页面，在扩展设置里确认：

```text
桥接地址  http://127.0.0.1:43121/v1
```

### TauriTavern

把本仓库放到：

```text
data/default-user/extensions/ST-bridge-tavern
```

或用它的 Git 扩展安装入口填本仓库地址，然后刷新页面。

## 配置

在扩展面板中：

- 启用「仅适配指定的本机桥接」；
- 填写桥接地址；
- 「按酒馆聊天自动隔离 DSH 会话」默认开启；
- 需要固定规则时再调固定规则条数/类型。

## 验证

发一条消息后查看桥接回执：

```powershell
curl.exe http://127.0.0.1:43121/v1/bridge/context/receipts
```

出现：

```json
{
  "adapter_state": "traced",
  "chat_id": "stb-<聊天ID>"
}
```

说明扩展已生效。

## 版本

当前扩展版本：`0.3.1`，对应 ST-bridge `0.9.x`。

## 许可

AGPL-3.0，见 [LICENSE](LICENSE)。
