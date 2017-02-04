---
title: "数据完整性"
layout: "post"
---

数据完整性（data integrity）意味着服务可用性和数据可访问性，二者缺一不可。

## 数据丢失故障

造成数据丢失的事故可以分类为三个因子的24种组合，这3个因子是：

* 根源问题：用户行为、管理员错误、应用程序bug、基础设施缺陷、硬件故障、自然灾害
* 影响范围：广泛、范围很窄
* 发生速度：快速发生、缓慢持续

## 保障数据完整性的方法

* 备份数据而不只是存档，交付的应该是一个恢复系统而不是备份系统
* 备份的多样性，如数据定期导出为其他格式
* 数据完整性是手段，数据可用性是目标
* Google SRE保障数据完整性的手段
  * 软删除：API调用时标记为已删除但实际数据依然存在，在某段时间之后再删除真实数据
  * 备份和恢复
    * 备份和还原的具体方法
    * 全量或增量备份的频率
    * 备份的存储位置
    * 备份的保留时间
    * 故障恢复的时间
  * 早期预警
    * 越早检测到数据丢失，数据的恢复就越容器
    * 带外数据校验
    * 确保数据恢复策略可以正常工作
  * 信任仍要验证
  * 经验性演习，不经常使用的系统组件一定会在最需要的时候出现故障
  * 纵深防御，多个保障手段彼此覆盖