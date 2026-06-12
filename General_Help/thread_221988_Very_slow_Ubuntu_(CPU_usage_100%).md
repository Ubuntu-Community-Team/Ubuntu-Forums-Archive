---
title: "Very slow Ubuntu (CPU usage 100%)"
date: 2006-07-24
forum: General Help
---

### Post by hashd on 2006-07-24
I installed Ubuntu Dapper Drake(i386) on my system(Asrock K8Upgrade, AMD Athlon 64 3400+, 1GB RAM, 2x 160GB SATA disk).

The install went fine however the system is pretty slow - I am getting high cpu load when doing nothing! (goes from 0% to 20% while I am not doing anything). If I move a window a bit the CPU usage goes to 100%.

I have nvidia drivers installed and they are working. The kernel is 2.6.15-23-386, tried it with a K7 image but it's the same.

Any ideas?

---

### Post by Bagnaj97 on 2006-07-24
open a terminal and type 'top' it shows which processes are using the most resources in terms of CPU and Memory.

---

### Post by hashd on 2006-07-24
Okay, when running 'top' and moving a window around the CPU usage of 'Xorg' and 'gnome-panel' goes up enormously.

---

### Post by arnieboy on 2006-07-24
> **hashd said:**
> I installed Ubuntu Dapper Drake(i386) on my system(Asrock K8Upgrade, AMD Athlon 64 3400+, 1GB RAM, 2x 160GB SATA disk).

The install went fine however the system is pretty slow - I am getting high cpu load when doing nothing! (goes from 0% to 20% while I am not doing anything). If I move a window a bit the CPU usage goes to 100%.

I have nvidia drivers installed and they are working. The kernel is 2.6.15-23-386, tried it with a K7 image but it's the same.

Any ideas?
if u see similar performance issues with windows XP as well (abnormally high boot up time, long startup time for softwares), then its a hardware issue (RAM/CPU). One of the laptops that I have has this issue.

---

### Post by Thirsteh on 2006-07-24
Ensure that Ultra DMA (UDMA) is properly enabled on your hard-drive using the 'hdparm' utility, Google it for a how-to. Low performance issues can often be caused by the drivers not being properly set up for ATAPI devices - I've had this problem with my harddrive on Windows XP SP2, which required the installation of "Intel Application Accelerator", however, I've never had similar problems on Linux. Anyway, this may be the cause -- you can also see what mode your drives are running in, if any of them says PIO, something's DEFINITELY wrong!

---

### Post by hashd on 2006-07-24
It detects both my SATA disk and mounts them as SCSI(/dev/sda and sdb), so DMA does not need to be enabled. I have it enabled for the DVD-RW though.

I am currently trying with SLAX(a live-cd distribution based on slackware), and well it works perfect -- a lot faster than Ubuntu, granted it does use KDE (maybe there is a problem with Gnome on Ubuntu?)

Any ideas appreciated. If I don't fix this today I am going to switch to some other distribution...

---

