---
title: "Ubuntu 16.04 on optimus laptop crashes with three monitors using nvidia-prime"
date: 2016-08-25
forum: General Help
---

### Post by frozenrouter on 2016-08-25
I am trying to connect my laptop(Quanta NL8B, with a fresh install of  xubuntu 16.04) to two external displays(one 1920x1080 using HDMI, and  another 1600x1200 using VGA), using the built in display(1920x1080) as a  third. This works fine with the integrated graphics, however after  installation of nvidia-prime and nvidia-361 the laptop will freeze upon  seconds of logging in to use the nvidia card when  more than one of the  monitors is configured for use. Once frozen, the only solution is to  hold down the power button rebooting the laptop and either using a tty  to switch to intel graphics or disconnecting a monitor.  I was able to  use all three monitors with bumblebee, however due to both performance  and it better suiting my use, nvidia-prime is the graphics-switching  solution I would like to be able to use.  Interestingly, everything  works fine with using just the laptop display connected to a single  external monitor, but not with both external monitors and the laptop  display disabled.

output of lspci:
```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)

```

command used to install nvidia drivers:
```

sudo apt-get install nvidia-prime nvidia-361

```

Bumblebee was previously set up using this quide:
[https://lenovolinux.blogspot.co.uk/2016/05/bumblebee-on-lenovo-t440p-nvidia-gt.html](https://lenovolinux.blogspot.co.uk/2016/05/bumblebee-on-lenovo-t440p-nvidia-gt.html)
While that was functional, performance was sub-par(windows was many  times faster, and with less input lag), hence my reason to clean install  and try to setup nvidia-prime.

Any help that you can offer would be much appreciated.

---

### Post by frozenrouter on 2016-08-29
Interestingly, after an apt-get purge of nvidia* and then installing  nvidia-prime and nvidia-361 again, i have no opengl when running the  nvidia card, but can now output to all three monitors. There is also now a popup on login saying that the system had experienced an error.
```

glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig


prime-select query
nvidia

```

---

