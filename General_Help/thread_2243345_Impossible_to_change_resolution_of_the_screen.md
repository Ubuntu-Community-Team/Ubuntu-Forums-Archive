---
title: "Impossible to change resolution of the screen"
date: 2014-09-08
forum: General Help
---

### Post by jacopo2207 on 2014-09-08
I have just installed Ubuntu-Gnome 14.04.01 on an Dell optiplex390. Everything seems to work fine, with the only exception of the screen resolution. I'd like to set it for a 16:9 screen (1920x1080), but it seems that the only resolution available is 1280 x 1024

```
jacopo@OptiPlex-390:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0*
```

I've already tried to install additional drivers following similar threads, without success.

Here are additional information

```
jacopo@OptiPlex-390:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```
and

```
jacopo@OptiPlex-390:~$ sudo lshw -C display; lsb_release -a; uname -a
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0c00000-e0ffffff memory:d0000000-dfffffff ioport:4000(size=64)
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
Linux jacopo-OptiPlex-390 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```



Thanks!

---

### Post by jacopo2207 on 2014-09-09
UPDATE

I typed the following commands

```
jacopo@OptiPlex-390:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
jacopo@OptiPlex-390:~$ xrandr --addmode default "1920x1080_60.00"
xrandr: Failed to get size of gamma for output default
jacopo@OptiPlex-390:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* 
   1920x1080_60.00   60.0  

```

Unfortunately I still get the error and I'm still not able to set the resolution of the screen to 1920x1080.

---

