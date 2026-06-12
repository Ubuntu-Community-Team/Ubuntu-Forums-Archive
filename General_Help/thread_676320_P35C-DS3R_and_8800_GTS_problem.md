---
title: "P35C-DS3R and 8800 GTS problem"
date: 2008-01-23
forum: General Help
---

### Post by bveb on 2008-01-23
Hi
My new computer has mobo P35C-DS3R with 2GB ram and 8800 GTS graphics card. All works fine with Gutst except vga card.. nv or nvidia-glx-new dont work.. I can only use with vesa driver @ 800x600 my dmesg says

```

[   51.266575] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   51.266580] NVRM: rm_init_adapter(0) failed
[   54.034296] NET: Registered protocol family 17
[   55.304767] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   55.304773] NVRM: rm_init_adapter(0) failed
[   57.580647] NET: Registered protocol family 10
[   57.580763] lo: Disabled Privacy Extensions
[   59.342264] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   59.342269] NVRM: rm_init_adapter(0) failed
[   68.355777] eth0: no IPv6 routers present
[  315.186396] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[  315.186401] NVRM: rm_init_adapter(0) failed
[  471.701799] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[  471.701805] NVRM: rm_init_adapter(0) failed
[  475.724082] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[  475.724087] NVRM: rm_init_adapter(0) failed
[  479.745725] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[  479.745731] NVRM: rm_init_adapter(0) failed

```

Also Xorg says input/output error on /dev/nvidia0 ,,,,

lspci output,,
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0600 (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)



```

Thanks..

---

### Post by bveb on 2008-01-27
When I try to install nvidia-glx-new package apt-get tries to install 386 kernel image.. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-restricted-modules-2.6.22-14-386 nvidia-kernel-common
Suggested packages:
  avm-fritz-firmware-2.6.22-14 nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
  linux-restricted-modules-2.6.22-14-386 nvidia-glx-new nvidia-kernel-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 5019kB/21.8MB of archives.
After unpacking 59.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n


I am using generic kernel.. what is the reason?? Dependency check doesnt work properly..

---

