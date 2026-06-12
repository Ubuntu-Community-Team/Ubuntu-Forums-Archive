---
title: "Suspension fails"
date: 2022-12-26
forum: General Help
---

### Post by OiPenguin on 2022-12-26
I've got a laptop which I'm fairly pleased with, however suspend (closing the lid) doesn't work reliably. More often then not all applications shuts down, be it the terminal or chrome. How do I solve this? (And which info about my hardware do you need to help me?)

Yours sincerely,

Lars 

```
uname -a
Linux lars-lenovo 5.19.0-26-generic #27-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov 23 20:44:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

```

sudo lshw -short
[sudo] password for lars: 
H/W path            Device          Class          Description
==============================================================
                                    system         82L7 (LENOVO_MT_82L7_BU_idea_
/0                                  bus            LNVNB161216
/0/0                                memory         128KiB BIOS
/0/4                                processor      AMD Ryzen 7 5800U with Radeon
/0/4/5                              memory         512KiB L1 cache
/0/4/6                              memory         4MiB L2 cache
/0/4/7                              memory         16MiB L3 cache
/0/22                               memory         16GiB System Memory
/0/22/0                             memory         8GiB SODIMM DDR4 Synchronous 
/0/22/1                             memory         8GiB SODIMM DDR4 Synchronous 
/0/100                              bridge         Renoir/Cezanne Root Complex
/0/100/0.2                          generic        Renoir/Cezanne IOMMU
/0/100/2.2                          bridge         Renoir/Cezanne PCIe GPP Bridg
/0/100/2.2/0        wlp1s0          network        MT7921 802.11ax PCI Express W
/0/100/2.3                          bridge         Renoir/Cezanne PCIe GPP Bridg
/0/100/2.3/0        mmc0            bus            RTS522A PCI Express Card Read
/0/100/2.4                          bridge         Renoir/Cezanne PCIe GPP Bridg
/0/100/2.4/0        /dev/nvme0      storage        WDC PC SN530 SDBPMPZ-512G-110
/0/100/2.4/0/0      hwmon3          disk           NVMe disk
/0/100/2.4/0/2      /dev/ng0n1      disk           NVMe disk
/0/100/2.4/0/1      /dev/nvme0n1    disk           512GB NVMe disk
/0/100/2.4/0/1/1    /dev/nvme0n1p1  volume         475MiB Windows FAT volume
/0/100/2.4/0/1/2    /dev/nvme0n1p2  volume         9537MiB EXT4 volume
/0/100/2.4/0/1/3    /dev/nvme0n1p3  volume         27GiB EXT4 volume
/0/100/2.4/0/1/4    /dev/nvme0n1p4  volume         14GiB Linux swap volume
/0/100/2.4/0/1/5    /dev/nvme0n1p5  volume         424GiB EXT4 volume
/0/100/8.1                          bridge         Renoir Internal PCIe GPP Brid
/0/100/8.1/0        /dev/fb0        display        Cezanne
/0/100/8.1/0.1      card0           multimedia     Renoir Radeon High Definition
/0/100/8.1/0.1/0    input14         input          HD-Audio Generic HDMI/DP,pcm=
/0/100/8.1/0.1/1    input15         input          HD-Audio Generic HDMI/DP,pcm=
/0/100/8.1/0.1/2    input16         input          HD-Audio Generic HDMI/DP,pcm=
/0/100/8.1/0.2                      generic        Family 17h (Models 10h-1fh) P
/0/100/8.1/0.3                      bus            Renoir/Cezanne USB 3.1
/0/100/8.1/0.3/0    usb1            bus            xHCI Host Controller
/0/100/8.1/0.3/0/3  input12         multimedia     Integrated Camera: Integrated
/0/100/8.1/0.3/1    usb2            bus            xHCI Host Controller
/0/100/8.1/0.4                      bus            Renoir/Cezanne USB 3.1
/0/100/8.1/0.4/0    usb3            bus            xHCI Host Controller
/0/100/8.1/0.4/0/4                  communication  Wireless_Device
/0/100/8.1/0.4/1    usb4            bus            xHCI Host Controller
/0/100/8.1/0.5      card2           multimedia     ACP/ACP3X/ACP6x Audio Coproce
/0/100/8.1/0.6      card1           multimedia     Family 17h/19h HD Audio Contr
/0/100/8.1/0.6/0    input17         input          HD-Audio Generic Mic
/0/100/8.1/0.6/1    input18         input          HD-Audio Generic Headphone
/0/100/14                           bus            FCH SMBus Controller
/0/100/14.3                         bridge         FCH LPC Bridge
/0/100/14.3/0                       system         PnP device PNP0c02
/0/100/14.3/1                       system         PnP device PNP0b00
/0/100/14.3/2                       generic        PnP device FUJ7401
/0/100/14.3/3                       system         PnP device PNP0c02
/0/100/14.3/4                       system         PnP device PNP0c01
/0/100/14.3/5       input8          input          Ideapad extra buttons
/0/101                              bridge         Renoir PCIe Dummy Host Bridge
/0/102                              bridge         Renoir PCIe Dummy Host Bridge
/0/103                              bridge         Renoir PCIe Dummy Host Bridge
/0/104                              bridge         Cezanne Data Fabric; Function
/0/105                              bridge         Cezanne Data Fabric; Function
/0/106                              bridge         Cezanne Data Fabric; Function
/0/107                              bridge         Cezanne Data Fabric; Function
/0/108                              bridge         Cezanne Data Fabric; Function
/0/109                              bridge         Cezanne Data Fabric; Function
/0/10a                              bridge         Cezanne Data Fabric; Function
/0/10b                              bridge         Cezanne Data Fabric; Function
/1                                  power          CRB Battery 0
/2                  input0          input          Lid Switch
/3                  input1          input          Sleep Button
/4                  input11         input          MSFT0004:00 04F3:31BE Touchpa
/5                  input2          input          Power Button
/6                  input3          input          AT Translated Set 2 keyboard
/7                  input4          input          Video Bus
/8                  input9          input          MSFT0004:00 04F3:31BE Mouse
user@pc:~$ 



```

---

### Post by OiPenguin on 2023-01-22
I'm still struggling with the issue described in the initial post and came across this thread. However, before attempting anything I'd like to get input from someone about this. Is it likely that the issue described in the thread is related to my problem? What would be a safe and feasible change of my system to try to mitigate my problem? As shown below, there should be no lack of ram or swap space in my system.
[https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html](https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html)

PC@PC-lenovo:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:            13Gi       5,7Gi       1,4Gi       247Mi       6,4Gi       7,3Gi
Swap:           14Gi       4,0Mi        14Gi

---

