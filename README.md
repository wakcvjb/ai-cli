# AI CLI

命令行AI助手，在Termux终端运行，支持8个免费AI平台。

## 目录

- [功能特点](#功能特点)
- [支持的平台](#支持的平台)
- [安装步骤](#安装步骤)
- [首次配置](#首次配置)
- [命令列表](#命令列表)
- [数据存储](#数据存储)
- [获取API密钥](#获取api密钥)
- [常见问题](#常见问题)
- [许可证](#许可证)

## 功能特点

- 完全免费，全部使用免费AI模型
- 支持8个AI平台，通过统一界面调用
- 中英文双语界面，启动时选择
- 每个模型按官方主题色显示
- 自动保存配置，下次启动无需重新设置
- 自动保存对话历史，格式为JSON
- 支持联网搜索（DuckDuckGo）
- 数据存储在 /storage/emulated/0/Download/ClaudeBox/
- 首次启动自动引导配置
- 对话中可随时切换模型和语言

## 支持的平台

| 平台 | 免费模型 | 说明 |
|------|----------|------|
| OpenRouter | 是 | 聚合平台，可路由到多个免费模型 |
| DeepSeek | 是 | 深度求索，代码能力强 |
| Qwen | 是 | 阿里通义千问 |
| Zhipu | 是 | 智谱GLM系列 |
| Kimi | 是 | 月之暗面Moonshot |
| Baichuan | 是 | 百川智能 |
| MiniMax | 是 | MiniMax对话模型 |
| Ollama | 是 | 本地模型，无需API密钥 |

## 安装步骤

### 1. 安装必要依赖

pkg update && pkg upgrade -y
pkg install curl nlohmann-json g++ make git -y

### 2. 授予存储权限（必须执行）

termux-setup-storage

执行后会弹出系统权限请求，点击允许。

### 3. 克隆项目

git clone https://github.com/wakcvjb/ai-cli.git
cd ai-cli

### 4. 给程序添加执行权限

chmod +x ai_cli

### 5. 运行

./ai_cli

## 首次配置

第一次运行时会自动进入配置流程：

### 第一步：选择语言

Select Language / 选择语言:
  1. English
  2. 中文
Select:

输入 1 或 2 选择界面语言。

### 第二步：选择AI平台

Select AI Platform (All Free):
  1. OpenRouter
  2. DeepSeek
  3. Qwen
  4. Zhipu
  5. Kimi
  6. Baichuan
  7. MiniMax
  8. Ollama

Select platform index:

输入对应数字选择平台。

### 第三步：输入API密钥

Enter API Key:

粘贴你的API密钥（输入时不会显示明文）。

如果是Ollama平台，无需输入密钥。

### 第四步：选择模型

Available models:
  1. openrouter/free
  2. meta-llama/llama-3.3-70b-instruct:free
  3. deepseek/deepseek-r1-0528:free
  4. google/gemini-2.0-flash-exp:free

Select model index:

输入数字选择具体模型。

配置完成后自动保存，下次启动直接进入对话。

## 命令列表

| 命令 | 说明 |
|------|------|
| /help | 显示帮助信息 |
| /model | 显示当前使用的模型 |
| /model N | 切换到第N个模型（N为数字） |
| /debug | 开启或关闭调试输出 |
| /search | 开启或关闭联网搜索 |
| /key | 重新输入API密钥 |
| /clear | 清空当前对话历史 |
| /history | 显示最近对话记录 |
| /lang | 重新选择界面语言 |
| /config | 重新进行完整配置 |
| /quit | 退出程序 |

## 数据存储

所有数据保存在 `/storage/emulated/0/Download/ClaudeBox/`

| 文件 | 说明 |
|------|------|
| config.json | 存储API密钥、当前模型、语言设置 |
| history.json | 存储完整对话历史（JSON格式） |

### config.json 示例

{
  "lang": "zh",
  "provider": "OpenRouter",
  "model": "openrouter/free",
  "api_keys": {
    "OpenRouter": "sk-or-v1-xxxxx"
  }
}

### history.json 示例

{
  "messages": [
    {"role": "user", "content": "你好"},
    {"role": "assistant", "content": "你好！有什么我可以帮助你的吗？"}
  ]
}

## 获取API密钥

| 平台 | 获取地址 |
|------|----------|
| OpenRouter | https://openrouter.ai/keys |
| DeepSeek | https://platform.deepseek.com/api_keys |
| Qwen | https://dashscope.aliyuncs.com/ |
| Zhipu | https://open.bigmodel.cn/ |
| Kimi | https://platform.moonshot.cn/ |
| Baichuan | https://platform.baichuan-ai.com/ |
| MiniMax | https://api.minimax.chat/ |

## 常见问题

### 1. 提示 Storage permission required

运行 termux-setup-storage 并允许存储权限。

### 2. 提示 Permission denied

chmod +x ai_cli

### 3. API密钥无效或过期

在对话中输入 /key 重新输入API密钥。

### 4. 模型返回错误

可能是免费模型限流，输入 /model 1 切换到 openrouter/free 自动选择可用模型。

### 5. 如何更新程序

git pull

### 6. 对话历史保存在哪里

/storage/emulated/0/Download/ClaudeBox/history.json

## 许可证

MIT License

Copyright (c) 2026 wakcvjb

## 作者

wakcvjb
