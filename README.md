# RTT-nanoFramework

> **让 C# 驱动工业硬核：基于 RT-Thread 睿擎生态的 .NET 高级语言实时运行环境**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![RT-Thread](https://img.shields.io/badge/RT--Thread-5.x%20%2F%20RedEngine-brightgreen.svg)](https://www.rt-thread.org/)
[![.NET Foundation](https://img.shields.io/badge/.NET-nanoFramework-blueviolet.svg)](https://www.nanoframework.net/)
[![Platform](https://img.shields.io/badge/Platform-Industrial%20Edge-orange.svg)](#)

---

## 📖 项目简介

**RTT-nanoFramework** 是一个将 **.NET nanoFramework**（受 .NET 基金会官方托管）深度移植并优化至 **RT-Thread** 实时操作系统及其 **睿擎 (RedEngine)** 工业平台的开源项目。

本项目由 **叶帆科技** 发起，旨在解决工业数字化转型中“人才断层”与“交付周期长”的痛点。通过在 RT-Thread 上构建 .NET 运行时，我们为工业领域引入了现代化的 **C#** 开发范式，让 IT 软件工程师能够像开发上位机一样，轻松编写嵌入式边缘计算逻辑。

---

## ✨ 为什么选择 RTT-nanoFramework？

* **🚀 IT 生产力降维打击：** 允许数百万 .NET 开发者使用 C#、LINQ、async/await 等高级特性开发工业设备，无需深究寄存器与 C 语言指针。
* **⏱️ 硬实时执行：** 基于 RT-Thread 5.x 内核，确保托管代码在虚拟机中运行的同时，底层中断和实时任务依然保持微秒级的确定性调度。
* **🛠️ 睿擎 (RedEngine) 深度赋能：** 原生适配睿擎工业开发平台，通过 C# 即可调用 EtherCAT、CANopen、Modbus 等高精度工业协议栈。
* **💻 极致开发体验：** 配合 Visual Studio 2022/2025，支持 **USB/网络实时断点调试**、变量监控和增量热部署，开发效率提升 3 倍以上。
* **🛡️ 安全与隔离：** 利用 .NET 托管堆栈和垃圾回收机制（GC），从物理上规避了内存泄露和非法指针导致的系统崩溃。

---

## 🏗️ 技术架构 (Architecture)

```mermaid
graph TD
    subgraph "应用层 (IT Friendly)"
        A1[C# 业务应用 / YFIOs Next]
        A2[边缘 AI 推理模块]
    end

    subgraph "RTT-nanoFramework (The Bridge)"
        B1[C# BCL 基础类库]
        B2[CLR 运行时 / 解释器]
        B3[HAL 硬件抽象层]
    end

    subgraph "RT-Thread / RedEngine (OT Hardcore)"
        C1[RT-Thread 5.x 内核]
        C2[睿擎工业协议栈]
        C3[底层驱动与总线]
    end

    A1 --> B1
    B1 --> B2
    B2 --> C1
    
    subgraph "开发环境"
    F[Visual Studio] -.->|Debugger| B2
    end
🎯 典型应用场景
钢铁/生产制造边缘 AI： 在产线旁实时采集数据并运行本地推理模型，实现预测性维护。

存量设备数智化改造： 快速开发支持多协议的边缘网关，满足“数据不出厂”的安全需求。

IT/OT 融合平台： 助力拥有软件团队的传统企业，通过 C# 快速构建自有的工业级控制器。

🚀 快速开始
1. 环境准备
安装 Visual Studio 2022/2025。

在 VS 中安装 .NET nanoFramework 扩展插件。

准备一块已刷入 RTT-nanoFramework 固件的 RT-Thread 开发板（如 STM32, ESP32 或 RISC-V 平台）。

2. 编写第一个 C# 工业程序
C#
'''
using System;
using System.Device.Gpio;
using System.Threading;

public class Program
{
    public static void Main()
    {
        // 操控由 RT-Thread 驱动的工业级 GPIO
        var controller = new GpioController();
        var relayPin = controller.OpenPin(15, PinMode.Output);
        
        Console.WriteLine("RTT-nanoFramework 启动成功！");

        while (true)
        {
            relayPin.Write(PinValue.High); // 继电器闭合
            Thread.Sleep(1000);
            relayPin.Write(PinValue.Low);  // 继电器断开
            Thread.Sleep(1000);
        }
    }
}
'''
🗓️ 2026 路线图 (Roadmap)
[x] 2025 Q4: 完成 RT-Thread 5.1 核心内核适配与 CLR 移植。

[x] 2026 Q1: 发布基于睿擎平台的 GPIO/UART/CAN 参考实现。

[ ] 2026 Q2: 深度支持 EtherCAT 协议栈的 C# 绑定与驱动。

[ ] 2026 Q3: 集成轻量化边缘 AI 推理引擎，支持本地模型执行。

[ ] 2026 Q4: 正式发布 YFIOs Next 面向钢铁与生产制造的低代码模板。

🤝 贡献与致谢
.NET nanoFramework: 感谢 José Simões 及其团队提供的卓越底层运行时框架。

RT-Thread 社区: 感谢睿赛德团队提供的国产优秀实时操作系统内核及睿擎生态支持。

叶帆科技: 本项目由叶帆科技团队焕新研发，致力于服务工业 4.0 数字化转型。

📄 开源协议
本项目基于 MIT License 开源。这意味着您可以自由地用于商业项目，无需公开您的核心业务逻辑源代码，对企业级闭源应用极其友好。

⭐ 如果这个项目对您有帮助，请点一个 Star！ 如有任何技术合作或商业咨询，欢迎通过 GitHub Issue 或访问 叶帆科技官网 联系我们。
