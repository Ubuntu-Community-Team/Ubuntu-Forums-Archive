---
title: "Poor video playback in Xubuntu 14.04 on an Asus X200MA"
date: 2015-07-06
forum: General Help
---

### Post by roquet2 on 2015-07-06
Videos play fine but when the image changes quickly, horizontal lines appear where the upper and lower part of the picture don't quite match up. You might call it choppy, not sure. Apart from that the video image is very good quality. I get same thing with VLC, Totem and Parole. 

I tried reducing swappiness from 60 to 10 and did the updates suggested here [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu#TOC-Apply-all-available-updates](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu#TOC-Apply-all-available-updates) but it didn't improve video playback.

Here are the result of > lshw -c video in Terminal:

> *-display               
       description: VGA compatible controller
       product: ValleyView Gen7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:108 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
 
Any ideas to get videos playing smoothly? Everything else works perfectly.

Thanks

---

### Post by speartip on 2015-07-06
If you google around, it seems video tearing is a common problem for xfce users. It was a deal breaker for me in an otherwise solid distro.
There are one or two things you could try. Many have had success with using compton as the window manager.
Arch has a good wiki for that:
[https://wiki.archlinux.org/index.php/Compton](https://wiki.archlinux.org/index.php/Compton)
There are also good instructions here with a config file as well:
[http://www.iwillfolo.com/how-to-use-compton-compositing-manager-to-enhance-xfce-lxde-other-des/](http://www.iwillfolo.com/how-to-use-compton-compositing-manager-to-enhance-xfce-lxde-other-des/)
It's not bad but occasionally causes other visual glitches.
See how you go. It's easy to revert back if your not happy.

---

### Post by roquet2 on 2015-07-08
Compton didn't improve video tearing for me. In fact it was worse than just enabling composting and "synchronize drawing to the vertical blank" in Windows Manager Tweaks.

I fixed the issue by making an Intel graphics driver file with TearFree enabled. To do this:

1. Make a file in the Home directory called "20-intel.conf", containing the lines: ```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "TearFree"    "true"
EndSection
``` 
2. Move "20-intel.conf" to the folder /usr/share/X11/xorg.conf.d using the Terminal command: ```
sudo mv 20-intel.conf /usr/share/X11/xorg.conf.d/
```
3. Restart computer.

Video playback is now perfect in VLC.

Here are the links I used.
[https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video](https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video)
[https://www.distroshare.com/distros/get/14/](https://www.distroshare.com/distros/get/14/)

---

### Post by speartip on 2015-07-09
Hi roquet2.
Good find. That seems to do the trick. Although compton worked for me, it did have one or two graphics glitches.
Could you just check something for me.
After applying the above fix, I am left unable to upgrade the package "libgbm1", saying I have broken dependencies.
Do you have the same issue?

edit.. Actually just to add a bit more to this. for me simply adding the "20-intel.conf" file solved the problem, without adding the ppa.

---

### Post by roquet2 on 2015-07-09
Software Updater ran without errors just now. I don't know if it upgrades the package "libgbm1" every time though.

I did wonder if the "20-intel.conf" file alone would fix video tearing. Unfortunately I added the ppa first. If I get "libgbm1" errors in the future I'll try removing the ppa and see if video still plays ok.

---

### Post by speartip on 2015-07-10
My software updater doesn't give any errors.
But when I look in synaptic libgbm1 is still to be upgraded, but when I try & upgrade it, I get the broken dependency error.
Although that ppa looks like it's being updated constantly so it may rectify itself.
Also if you hit any issues with the ppa, you van downgrade simply to the official packages by,
```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```

---

### Post by roquet2 on 2015-07-11
Ok, I see what you mean. I get the same errors trying to update libgbm1 in Synaptic. So I got rid of the new graphics drivers with the commands above and video still plays fine. I'll amend my previous post. accordingly.

---

