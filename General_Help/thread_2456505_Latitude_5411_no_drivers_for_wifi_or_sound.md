---
title: "Latitude 5411 no drivers for wifi or sound"
date: 2021-01-12
forum: General Help
---

### Post by horizn on 2021-01-12
I have Installed Kubuntu 20.04 LTS on Dell Latitude 5411 laptop ([https://certification.ubuntu.com/hardware/202002-27717](https://certification.ubuntu.com/hardware/202002-27717)) but unfortunately there are no sound and wifi card drivers installed. Weirdly wifi was working for sure during the installation process. Looks like something wasn't installed properly. How can I fix it?

---

### Post by gdesilva on 2021-01-13
Post the output from 'lspci' command here so that people can make suggestions to fix your issue - it is possible that your laptop may actually contain different hardware?

---

### Post by jeremy31 on 2021-01-13
Post results from terminal for ```
dpkg -l | grep linux-modules-extra-$(uname -r)
```

---

### Post by Yellow Pasque on 2021-01-14
Seeing as how it's very new hardware (Comet Lake), you should try the newer HWE kernel before anything else:
```
sudo apt-get install linux-generic-hwe-20.04
```

---

### Post by horizn on 2021-01-14
> **gdesilva said:**
> Post the output from 'lspci' command here so that people can make suggestions to fix your issue - it is possible that your laptop may actually contain different hardware?

```

00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 02)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x8) (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Comet Lake PCH Thermal Controller
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.1 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #1
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:16.3 Serial controller: Intel Corporation Device 06e3
00:17.0 SATA controller: Intel Corporation Device 06d3
00:1c.0 PCI bridge: Intel Corporation Device 06b8 (rev f0)
00:1c.5 PCI bridge: Intel Corporation Device 06bd (rev f0)
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 068e
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (11) I219-LM
02:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX250] (rev a1)
03:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
04:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
05:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3b:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3c:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
3d:00.0 Non-Volatile memory controller: Micron Technology Inc Device 5405

```

---

### Post by horizn on 2021-01-14
> **jeremy31 said:**
> Post results from terminal for ```
dpkg -l | grep linux-modules-extra-$(uname -r)
```

it returns nothing.

---

### Post by horizn on 2021-01-14
> **Yellow Pasque said:**
> Seeing as how it's very new hardware (Comet Lake), you should try the newer HWE kernel before anything else:
```
sudo apt-get install linux-generic-hwe-20.04
```

This did the trick! Thanks.

---

