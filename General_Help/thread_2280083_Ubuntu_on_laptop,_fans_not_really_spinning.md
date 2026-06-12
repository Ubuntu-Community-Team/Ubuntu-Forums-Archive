---
title: "Ubuntu on laptop, fans not really spinning"
date: 2015-05-28
forum: General Help
---

### Post by cwblanch on 2015-05-28
Hey,

so I've just installed Ubuntu 14.04 on my laptop, and I've only just noticed that my laptop is getting really hot!
I've installed xsensors and the "acpitz" temp occasionally drops to about 58 degrees celsius but usually hovers around 60-65. The k10temp stays in the high 50s and low 60s, and radeon is 57-62

It seems like most of the time the fan isn't even spinning and everynow and it I hear it spin up for a minute. When I'm using windows my computer doesn't feel this hot and the fans periodically spin up.

I've done some googling but I haven't found much for non dell computers, I'm also not sure how to make the fans spin.

I have an AMD A6 APU and I'm actually having a hard time finding system info in Ubuntu MATE. If you need anymore info I'll get it and any help would be appreciated.

Thanks!

---

### Post by Bucky Ball on 2015-05-28
Please provide the make/model of your machine.

System info =

```
lspci
```

... in a terminal.

---

### Post by mastablasta on 2015-05-28
I've noticed this on a very OLD ATI card. the fan just doesn't start to spin. I think I will report it as a bug once I have the time to gather more info.

before computer was relatively loud, now it is relatively quiet but the GPU card CPU rarely if ever spins up.

---

### Post by RobGoss on 2015-05-28
I don't see how this can be related to Ubuntu sounds like a hardware problem on that machine your using

Question? What OS did you have on this machine before you installed Ubuntu and did you notice the same problem.

---

### Post by mastablasta on 2015-05-28
can't be hardware issue as OP says it works OK on Windows.

---

### Post by cwblanch on 2015-05-28
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


```

this is the output from lspci

And the make/model is Toshiba Satellite C855D

---

### Post by NoWayWin8 on 2015-05-28
have you installed `thermald'?

---

### Post by cwblanch on 2015-05-28
> **NoWayWin8 said:**
> have you installed `thermald'?

I hadn't run across that in my searches, but I'll give it a shot. 
Thanks

---

