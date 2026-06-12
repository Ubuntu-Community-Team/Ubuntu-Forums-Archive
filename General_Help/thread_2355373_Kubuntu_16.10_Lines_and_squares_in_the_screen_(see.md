---
title: "Kubuntu 16.10 Lines and squares in the screen (see snapshots)"
date: 2017-03-12
forum: General Help
---

### Post by el-ruby on 2017-03-12
[COLOR=#111111][FONT=Ubuntu]Problem: Lines and squares in the login screen and desktop (see the snapshots).
[/FONT][/COLOR]
> Computer:  
Microserver HP n54l 
Asus R7 240
Driver: amdgpu-pro 
OS: Kubuntu 16.04.2 LTS (Xenial Xerus) with kernel 4.4.2.

[COLOR=#111111][FONT=Ubuntu]Upgrade the kernel to 4.8 don´t solve the issue.
Upgrade to 16.10 (Yakkety Yak) don´t solve the issue.
I try with OpenGL 2.0, 3.1 and Xender and the same problem.
I try with all the options of "vsync" and the same problem.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Change the config files>  /usr/share/X11/xorg.conf.d/10-amdgpu-pro.conf and > /usr/share/X11/xorg.conf.d/10-amdgpu.conf with:[/FONT][/COLOR]
> Option "DRI3" "1"
Option "TearFree" "on"
[COLOR=#111111][FONT=Ubuntu]The same problem.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My computer now:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 16.10 (GNU/Linux 4.8.0-41-generic x86_64)
[/FONT][/COLOR]
> lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340] (rev 87)

[HR][/HR]> lshw -C display
*-display
descripción: VGA compatible controller
producto: Oland PRO [Radeon R7 240/340]
fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
id físico: 0
información del bus: pci@0000:01:00.0
versión: 87
anchura: 64 bits
reloj: 33MHz
capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
configuración: driver=amdgpu latency=0
recursos: irq:27 memoria:d0000000-dfffffff memoria:fe8c0000-fe8fffff ioport:e000(size=256) memoria:c0000-dffff

[COLOR=#111111][FONT=Ubuntu]Thanks.
[ATTACH=CONFIG]274091[/ATTACH][ATTACH=CONFIG]274092[/ATTACH]

[/FONT][/COLOR]

---

### Post by RobGoss on 2017-03-12
Have you tried **16.04.2** it's a LTS release and a much better choice in my option and will be supported for a few more years. It looks a graphic card issue 

Try installing the propriety drives provided by Ubuntu **Software & updates**, then choose **Additional drivers**, let it scan and choose the appropriate drivers for your system

---

### Post by el-ruby on 2017-03-12
Before upgrade to 16.10 I had 16.04.02 and i have the same problem. The problema was the reason for the upgrade to 16.10.
The graphic card is new, berfore this I had a Nvidia.
In the drivers screen I only see the processor, see the snapshot.
[ATTACH=CONFIG]274093[/ATTACH]

---

### Post by Perfect Storm on 2017-03-12
To me it looks like the videocard is running on last breath. A faulty card perhaps.

---

### Post by el-ruby on 2017-03-12
I bought it to amazon the last week, i´m going to change it for ahother one.
I´m going to keep the thread open till I try the new one.
Thanks.

---

