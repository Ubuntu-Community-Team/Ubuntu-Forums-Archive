---
title: "xserver prob"
date: 2007-06-30
forum: General Help
---

### Post by nate_nightroad on 2007-06-30
hey fellas, i dont have tis problem until i update my ubuntu 7.04 32bit just now...then after i update ubuntu, i restart it and when i start ubuntu a blue screen pop up saying tat the xserver is not configure properly...so i start ubuntu in recovery mode and i reconfigure xserver from there...after configuring, i start ubuntu in normal mode but the same blue screen appear saying tat my xserver is not configure properly....

so any advice....thanks and have a nice day

---

### Post by justtech on 2007-06-30
Are you running an NVidia video card?

---

### Post by nate_nightroad on 2007-06-30
yea.....why??

u know the solution?

---

### Post by justtech on 2007-06-30
Yes, I had the same problem yesterday after the update.  I think this will fix your problem.
> 
 There's more than one way to handle this but I'd do the following:

sudo nano ect/X11/xorg.conf

Find where the following section. Yours may differ from this one.

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

change "nvidia" to "nv" and save the file.

When you reboot you shoild have X with the open source driver. Now I use synaptic to install the appropriate nvidia-glx package. This should get you in sync with the Ubuntu repositories. You may need to edit /etc/X11/xorg.conf again to say "nvidia".

You can find the full tread [here]("http://ubuntuforums.org/showthread.php?t=488066")

---

### Post by nate_nightroad on 2007-06-30
thanks dude....problem solved....
btw the code for terminal should be
sudo nano /etc/X11/xorg.conf

not

sudo nano ect/X11/xorg.conf

---

