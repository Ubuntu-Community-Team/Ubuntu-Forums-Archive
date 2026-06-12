---
title: "can't boot into GUI due to VMWare"
date: 2013-12-22
forum: General Help
---

### Post by dwlamb on 2013-12-22
[FONT=system]Something very weird has happened and I am at a loss to explain how.  The only thing I can think of is the installation of VMWare Tools is the culprit.

Yesterday I installed VMWare Player on Kubuntu 12.04.  For some reason today, my system spontaneously rebooted when I opened a new tab in Chrome.  During the boot process, I saw a message go past in terminal mode something to the effect "VMWare blocking file system" then was prompted with a TTY log-in. The gui interface is not available.

Subsequent reboots have not shown that message on the screen and I continue to be prompted only with a TTY log-in.  

After some troubleshooting looking at the syslog and xorg.0.log I have determined the X server is not working properly.  There is also this message on screen if I key in[/FONT] [FONT=courier new]sudo startx[/FONT][FONT=system]: [/FONT]

[FONT=courier new]NVIDIA: API mismatch: the NVIDIA kernel module has version 304.88, but this NVIDIA driver component has version 304.107.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

Fatal server error:
no screens found [/FONT]  

[FONT=system]Opening the xorg.conf file all I see is this:[/FONT]
[FONT=courier new]
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection[/FONT]


[FONT=system]This sure does not look good.   He[/FONT][FONT=system]lp for guidance how to fix this will be greatly appreciated.[/FONT]

---

### Post by dcstar on 2013-12-22
Most likely nothing to do with VMware. You probably have installed a new Nvidia driver that is not compatible with your current kernel.

Try booting from the previous kernel and see what happens.

---

### Post by dwlamb on 2013-12-23
That would be a challenge for my system does not present me with the menu to choose which kernel to boot from. :(

---

