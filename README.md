# <img src="app/appicon.svg" alt="PreySense logo" width="42" height="42" align="left"> PreySense 中文版

PreySense 是一款面向宏碁掠夺者（Acer Predator）笔记本的轻量级 Windows 硬件控制工具，源自 [hammadzaigham/PreySense](https://github.com/hammadzaigham/PreySense)（其本身 fork 自 G-Helper）。它可以快速、直接地控制性能模式、风扇、GPU 超频、RGB 灯效、屏幕选项与自定义硬件监控叠加层，彻底摆脱臃肿的官方 Predator Sense 软件。

> **本仓库为简体中文汉化版本**：基于上游 v1.4.0 进行全量界面汉化，不改变任何功能与交互逻辑。

本项目的开发面向特定硬件，兼容性未经全面验证：仅在有限的宏碁掠夺者机型上完成开发与测试，因此无法保证其他宏碁笔记本同样可用。

<p align="center">
  <img src="docs/pics/Prey Sense.png" alt="Prey Sense Interface" width="380"><br>
  <b>PreySense 主界面</b>
</p>

## 功能特性

- **性能模式**：在 **节能**、**静音**、**均衡**、**性能**、**极速** 之间快速切换。
- **按模式自定义**：每个模式可独立配置 CPU 功耗限制、GPU 偏移与自定义风扇曲线（风扇曲线中按住 Ctrl 可吸附数据点）。
- **CPU 与 GPU 调校**：
  - 直接控制 CPU 功耗限制（PL1 / PL2）。
  - NVIDIA GPU 核心与显存频率超频偏移。
- **GPU 模式切换**：在 **核显模式**（仅核显）、**标准模式**（核显 + 独显）与 **独显直连**（独显独占）之间切换，并支持电池供电时自动切换核显。
- **掠夺者键集成**：完整支持物理模式切换键与自定义快捷键，使用掠夺者键 + 1~5 即可切换性能模式。
- **屏幕配置**：自动切换刷新率、LCD 超频驱动（OD）控制与刷新率色彩配置。
- **电池管理**：充电上限控制，保护电池寿命。
- **键盘 RGB 控制**：支持键盘灯效调节。
- **紧凑硬件叠加层**：可定制的 HUD，实时显示 CPU/GPU 温度、风扇转速、功耗、内存/显存占用、FPS 计数器与功耗曲线图。

<p align="center">
  <img src="docs/pics/Overlay.png" alt="Prey Sense Overlay" width="380"><br>
  <b>硬件性能叠加层</b>
</p>

## 使用要求

- **操作系统**：Windows 10 或 Windows 11 x64。
- **硬件**：具备可用 Acer WMI 与 AcerService 接口的宏碁掠夺者笔记本。
- **运行时**：Microsoft [.NET 10 桌面运行时 x64](https://dotnet.microsoft.com/download/dotnet/10.0)。
- **CPU 调校**：需安装 [PawnIO](https://pawnio.eu/) 驱动，以访问底层 CPU MSR / 功耗限制。
- **RGB 调校**：需安装掠夺者服务组件（Predator Sense 相关服务），用于键盘 RGB 控制。

## 下载与运行

1. 下载最新版本。
2. 以管理员身份运行 `PreySense.exe`。

## 从源码构建

前置条件：安装 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)。

```powershell
dotnet build app\PreySense.csproj
```

打包单文件可执行程序：

```powershell
.\.github\publish.ps1
```

产物位于 `publish\PreySense\PreySense.exe`（需目标机器安装 .NET 10 桌面运行时）。

## 技术文档

关于 WMI 调用、寄存器偏移与灯效控制的详细说明（英文）位于 `docs` 目录：

- [Acer WMI 文档](docs/acer_wmi_documentation.md)
- [Acer 服务 RGB 协议](docs/acer_service_rgb.md)
- [已探明的 WMI 偏移](docs/discovered_offsets.md)

### 注册表状态

用户配置、自定义风扇曲线与应用状态保存在：

```text
HKCU\SOFTWARE\PreySense
```

## 参与贡献

欢迎提交贡献，尤其是以下方向：

- 更多宏碁掠夺者机型的硬件兼容性报告。
- WMI 与 AcerService 数据包文档。
- 针对不受支持硬件的安全回退方案。
- 界面美化、样式与无障碍改进。
- 中文汉化中的翻译修正与用词建议。

报告问题或提交改动时，请附上你的**笔记本型号、BIOS 版本、Windows 版本与 GPU 模式**。

## 免责声明

PreySense 会控制笔记本的底层硬件行为（风扇、功耗限制、频率）。请自行承担使用风险，错误的设置可能导致系统不稳定或异常行为。

## 上游与致谢

- 原项目：[hammadzaigham/PreySense](https://github.com/hammadzaigham/PreySense)
- 灵感来源：[G-Helper](https://github.com/seerge/g-helper)

本汉化版本在原项目基础上仅进行界面文字的中文化与字体适配，原作者及贡献者的版权与许可声明均予以保留。

## 开源许可

本项目基于 [MIT 许可证](LICENSE) 发布。

Copyright (c) 2026 PreySense contributors
