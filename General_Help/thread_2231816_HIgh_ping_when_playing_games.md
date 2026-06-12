---
title: "HIgh ping when playing games"
date: 2014-06-28
forum: General Help
---

### Post by blahh2 on 2014-06-28
I just switch from WIndows 7 to lubuntu and theres one thing that's bothering me, for some reason my ping is high when playing games. When i do normal stuff like browse the web watch videos and download stuff it's fine, but once i open a game and start playing i get 300-1000 ping and it's unplayable cause of the extreme lag. when i had windows i had maybe 20-40 ping now with linux i have 60-1000 ping i sometimes go down to like 60-100 but then after like 2 seconds it spikes up. Any way to fix this?:(

---

### Post by nerdtron on 2014-06-28
What programs are you running on the background? Maybe the update manager is running?

---

### Post by blahh2 on 2014-06-28
Nah i'm not running any programs in the background and no update manager isn't running

---

### Post by oCyiIsejN9jk on 2014-06-28
Hi, what is your hardware specifically? Please open a terminal and post the output of "lspci -nn" Thanks! :KS

---

### Post by blahh2 on 2014-06-28
> **Aaron_R._Durland said:**
> Hi, what is your hardware specifically? Please open a terminal and post the output of "lspci -nn" Thanks! :KS

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6250] [1002:9804]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
00:15.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

---

### Post by oCyiIsejN9jk on 2014-06-29
Hi,  are you running AMD's driver (fglrx) or the open source radeon driver? You can try running "top" in a terminal to see what process are running and CPU and memory loads. :)

---

### Post by blahh2 on 2014-06-29
> **Aaron_R._Durland said:**
> Hi,  are you running AMD's driver (fglrx) or the open source radeon driver? You can try running "top" in a terminal to see what process are running and CPU and memory loads. :)

No i'm not running anything in the background i know not to keep stuff running in the background, and even if i did have something running in the background i don't think that would effect my internet speed/ping

---

### Post by oCyiIsejN9jk on 2014-06-29
Ok, my mistake, I misunderstood what you meant by ping. Since it was better under Windows, I doubt it's bandwidth throttling. You could check out the solutions by Double_DeluXe at the bottom of this thread: [http://dev.dota2.com/showthread.php?t=97994](http://dev.dota2.com/showthread.php?t=97994)   You can also look around to see if anyone has a solution: [https://encrypted.google.com/#q=high+ping+while+gaming+linux&safe=active](https://encrypted.google.com/#q=high+ping+while+gaming+linux&safe=active)

---

