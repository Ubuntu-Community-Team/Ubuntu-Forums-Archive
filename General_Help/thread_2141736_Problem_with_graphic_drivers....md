---
title: "Problem with graphic drivers..."
date: 2013-05-03
forum: General Help
---

### Post by Lateralus138 on 2013-05-03
Hi all, I tried installing Nvidia drivers in Ubuntu 12.10 and after I restarted Unity was gone and all I could see was desktop shortcuts, no Conky or anything else. I then ran the nvidia-xconfig and it said to restart the server so I ran 

```
sudo service lightdm restart 
```

 and I got impatient and went to a new screen (ctrl+alt+F1) and logged in as root and ran 

```
startx
```

I then rebooted and now it can't get it to open in my normal 1366x768 resolution. It is in 640x480 I beleive.

Please help me learn what I have done wrong and hwo to fix it. Was it because I ran startx as root? Anyway I uninstalled the Nvidia driver with 

```
sudo apt-get remove --purge nvidia-current
```

and it didn't fix it. Please help!!

---

### Post by kc1di on 2013-05-03
First tell us what Nvidia video card your Using.
if your not sure type the following in a terminal
without the quotes "lspci"

---

### Post by Lateralus138 on 2013-05-03
Yeah sorry, should've have known to put that. It's just an onboard chip: Intel Corporation Mobile 4 Series Chipset (Gm45 on the Toshiba Satellite m505-s4940).

---

### Post by kc1di on 2013-05-03
if it's intel it would not use Nvidia driver.

why did you install nvidia?

---

### Post by Bashing-om on 2013-05-03
Lateralus138; Hi ...

Intel !== Nvidia graphics card.. Let us make sure we are on the right page;
Post the output of these terminal codes to see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```[INDENT=2]
good place to start

[/INDENT]

---

### Post by Lateralus138 on 2013-05-03
> **Bashing-om said:**
> Lateralus138; Hi ...

Intel !== Nvidia graphics card.. Let us make sure we are on the right page;
Post the output of these terminal codes to see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```[INDENT=2]
good place to start

[/INDENT]




  *-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:a400(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fdc00000-fdcfffff
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:ff40]
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by CatKiller on 2013-05-03
> **Lateralus138 said:**
> Intel=Nvidia
AMD=ATI

That's not even remotely true. AMD bought Ati, but Intel has nothing to do with Nvidia.

---

### Post by QIII on 2013-05-03
Hello!

Intel = Intel
Nvidia = Nvidia
AMD/ATI = AMD/ATI

According to your output, the i915 driver module is loaded and in use.  That is the Intel driver.

Installing the Nvidia driver and attempting to make adjustments through Nvidia's GUI may have created an xorg.conf file that is now interfering. 

Check to see if /etc/X11/xorg.conf exists.  If so, rename it to /etc/X11/xorg.conf.BAK and try rebooting.


Regards

---

### Post by Lateralus138 on 2013-05-03
> **CatKiller said:**
> That's not even remotely true. AMD bought Ati, but Intel has nothing to do with Nvidia.


Thanks for the info. That means for almost 15 years I have been  misled by endless articles and conversations with fellow COD/RTCW  texture builders about the war between Intel/Nvidia and AMD/ATI.  Although every system I have seen if it is Intel it usually has Nvidia  and if it is AMD it has ATI, with a few exceptions of custom built  machines. Maybe one is more often compatible with one than the other?





> **QIII said:**
> Hello!

Intel = Intel
Nvidia = Nvidia
AMD/ATI = AMD/ATI

According to your output, the i915 driver module is loaded and in use.  That is the Intel driver.

Installing the Nvidia driver and attempting to make adjustments through Nvidia's GUI may have created an xorg.conf file that is now interfering. 

Check to see if /etc/X11/xorg.conf exists.  If so, rename it to /etc/X11/xorg.conf.BAK and try rebooting.


Regards

I had thought about that, but forgot the path, will go delete it now....

---

### Post by QIII on 2013-05-03
By Intel/Nvidia, the authors probably meant that the two corporations, Intel and Nvidia, compete against ATI - which was formerly an independent corporation and is now owned by AMD and often referred to as AMD/ATI to differentiate it from the former ATI.

Intel, Nvidia and AMD/ATI all produce graphics controllers.

---

### Post by Lateralus138 on 2013-05-03
Worked perfect thanks!

---

### Post by Lateralus138 on 2013-05-03
> **QIII said:**
> By Intel/Nvidia, the authors probably meant that the two companies, Intel and Nvida, compete against ATI - which was formerly an independent company and is now owned by AMD.

Intel, Nvidia and AMD/ATI all produce graphics controllers.

Ok thanks. I know AMD was talking about owning ATI for many, many years.

---

### Post by kc1di on 2013-05-04
Also I would issue this command in a terminal.
```
sudo apt-get purge nvidia
```

---

### Post by Lateralus138 on 2013-05-04
OK thanks, is that just to clear any traces of Nvidia? It seems to be working fine as we speak, but I'll do it anyway.

---

