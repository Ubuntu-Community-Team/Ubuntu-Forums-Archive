---
title: "Problem:Dual Boot with windows 8 and Ubuntu 13.04 login problem in UEFI mode with amd"
date: 2013-06-01
forum: General Help
---

### Post by ShiddiQ on 2013-06-01
First i had a problem in dual booting(win8+Ubuntu13),after reading this forums i install boot-repair and cleared it.
now i installed amd dual graphics driver from AMD website:"amd-catalyst-13.4-linux-x86.x86_64"

Lap Detail:HP Pavilion g6 amd A8 Processor with Radeon Graphics hybrid.
when i check in terminal "fglrxinfo",it works fine and it shows my on board graphics 7640 and my hybrid graphics is 7670
and both can be switchable and working fine,Now the problem is when i start or restart my HP LAP 
I had a problem in logging and in sometimes if i add or install any softwares....And then when i restart or log Out 

"there is a blank black screen ,no commands is working,and i left it for half an hour then i need there to force shutdown by power butn or hard reset"

But Sometimes there is no problem in logging ,but when i installed any new software or something ,there occur a problem 
if i restart no ubuntu splash screen will shown,it shows only a black screen for long time.

I Can't find whats the problem.Please help me ....
Most of the time there is a problem,rarely or unfortunately sometime it works

I cant find any error message while logging or booting,I cant determine whether the problem is with 
1.Amd graphic driver downloaded from AMD website:"amd-catalyst-13.4-linux-x86.x86_64" or
2.Installing Boot-repair


lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7640G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M] (rev ff)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

