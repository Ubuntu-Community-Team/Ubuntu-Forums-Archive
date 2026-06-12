---
title: "Messed up computer installing Beryl"
date: 2007-01-10
forum: General Help
---

### Post by darweth on 2007-01-10
Hello.  I was attemping to install Beryl earlier and I messed up.  Cannot get into gdm now.  Only tty1.

To begin with... I didn't go into tty1 while doing these commands (probably dumb)

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev 
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common sudo rm /etc/init.d/nvidia-* 
sudo /etc/init.d/gdm stop 
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run 
sudo nvidia-xconfig --add-argb-glx-visuals 
sudo /etc/init.d/gdm start
```

Anyway... when I rebooted, I thought I could continue on with sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run in tty1 but it tells me that it can't open it.  I have mounted my hd on this live disc and verified that it is in the home directory.  What is going on?

I try sudo /etc/init.d/gdm start on its own and it says "OK" but nothing comes up.  I guess my xorg or x-config is messed up.

If I continue to be unable to get sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1 to work, how can I correct this damage to bring up X Windows and GDM under my old settings?

Thanks.

---

### Post by darweth on 2007-01-10
Hrm. Because of my dinky fonts and still not recognizing the difference between a 1 and a l with Sans, I think the problem is that I am typing an L in NVIDIA-Linux-x86-1.0-9631-pkg1.run after pkg.  hehe.  I will not boot up again and try.  It should work, I assume.

Can I still have directions for restoring stuff the old way with my old drivers and settings if it doesn't?

---

### Post by JamesWP on 2007-01-10
Don't know about restoring old settings and stuff, but if you press TAB after typing the first few letters it auto completes it for you, so just put the NVIDIA file in your home directory, and type in 'sudo sh NV' then hit tab, saves you having to type out and guess full names :-).

---

