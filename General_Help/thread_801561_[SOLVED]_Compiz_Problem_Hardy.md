---
title: "[SOLVED] Compiz Problem Hardy"
date: 2008-05-20
forum: General Help
---

### Post by Old_Grey_Wolf on 2008-05-20
Trying to start Compiz. Get the following:

> owner@owner-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


How do I fix the unsupported value at path ...

---

### Post by Old_Grey_Wolf on 2008-05-20
More information.

lshw -C display vive me:

>  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


---

### Post by tommyhakinen on 2008-05-21
> [http://ubuntuforums.org/showthread.php?t=709672&highlight=intel+mobile+GM965%2FGL960+compiz&page=2](http://ubuntuforums.org/showthread.php?t=709672&highlight=intel+mobile+GM965%2FGL960+compiz&page=2)
hope can help

---

### Post by Forlong on 2008-05-21
> **Old_Gray_Wolf said:**
> How do I fix the unsupported value at path ...
See my [bug report]("https://bugs.launchpad.net/bugs/209207"). Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.


P.S. please use more descriptive thread titles in the future. Thank you.

---

### Post by Old_Grey_Wolf on 2008-05-21
I deleted and reinstalled compiz & emerald, compared setting with a working computer, and got it working. I'm not sure exactly what I did that made it work. 

Thanks anyway for the support.

---

