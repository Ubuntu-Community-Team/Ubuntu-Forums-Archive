---
title: "Ubuntu 12.04 LTS Keeps locking up and running very slow"
date: 2013-11-06
forum: General Help
---

### Post by rcaca0 on 2013-11-06
Hello,

I recently upgraded from the last LTS to 12.04 LTS.  I noticed that my computer was running slow and also noticed that it would lock up on me and I would have to cycle the power to my computer.  Is there a Ctrl-Alt-Delete function so I can see what's running and what is locking up the computer?  Any ideas on what I can look for to see what is causing my computer to lock up or run slow.  I didn't have these problems before on the last LTS version of Ubuntu.  I would normally just reinstall the OS but I am trying to avoid this.  

My computer:
Motherboard: Asus M3A78
CPU: AMD 4 cores ((I think Phenom) 2.2 Ghz 
Dual 22 inch Acer Monitors
Video Card: Nvidia Geforce 9500 GT (01:00.0 VGA compatible controller  [0300]: NVIDIA Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)

Output from lspci -nn

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port C) [1002:597c]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)


Thanks,
R

---

### Post by drmrgd on 2013-11-06
The equivalent to the Task Manger in Windows would be the System Monitor.  In Kubuntu, I can access it with 'Ctrl+escape'.  Not sure if there's an equivalent in Ubuntu, but you can probably launch it with 'Alt+F2' and typing the name.  You can also check from the terminal with the 'top' command (or better - install htop).

Oh, just had a quick search, and here's some more info on System Monitor in Ubuntu:

[http://askubuntu.com/questions/95192/what-is-the-equivalent-of-control-alt-delete](http://askubuntu.com/questions/95192/what-is-the-equivalent-of-control-alt-delete)

---

### Post by buzzingrobot on 2013-11-06
Tap the Windows key, starting typing "System Monitor" and the search tool will display its icon.

---

### Post by rcaca0 on 2013-11-06
Cool Thanks.

---

