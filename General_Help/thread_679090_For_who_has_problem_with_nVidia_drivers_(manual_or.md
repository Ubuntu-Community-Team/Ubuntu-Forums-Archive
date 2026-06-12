---
title: "For who has problem with nVidia drivers (manual or apt installation)..."
date: 2008-01-26
forum: General Help
---

### Post by xx_shade_xx on 2008-01-26
Well (sorry if this post already exists).
I've installed Ubuntu Gusty on a "HP Pavillion 2Ghz 512Mo of RAM", and it worked fine without any changes.
When I tried to install nVidia drivers, the X server would come back until I reboot.
After, there was no way that the X server would reboot until I reinstall the nVidia drivers manually.
After some searches which didn't give results, I've finally solved my problem:
-install nVidia drivers
-do NOT let the nvidia-installer modify /etc/X11/xorg.conf file and make backup manually
-add manually in section "Device" : 
     Option     "AddARGBVisuals"          "True"
     Option     "AddARGBGLXVisuals"     "True"
and modify "nv" by "nvidia"
(for compiz-fusion users, add at the end;

Section "Extensions"
     Option     "composite"
EndSection

)
-Now, you reboot gdm/kdm, and it works fine. But after rebooting, X cries that xorg.conf is not usable... but it is not this file! It seems that nvidia module is not loaded correctly.
Then I've added some lines into /etc/rc3.d/S30gdm (I think it is not a good idea, but it works ^^) under "set -e":

/sbin/modprobe -r nvidia
/sbin/modprobe nvidia
/sbin/ldconfig
/sbin/depmod -aq


Now, your X session can use the nVidia driver correctly, without X crashes. If you find an other file where add all "/sbin/..." lines (before loading gdm), please tell me!

Believing it will help you, dear Ubuntu users.

---

### Post by Mikecore on 2008-01-27
I don't recommend anyone follow what he posted. 

Please follow this link for the official install guide

```

https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29

```

Please follow this if you want to manually install your Nvidia driver.

```

https://help.ubuntu.com/community/NvidiaManual?highlight=%28nvidia%29

```

I know your only trying to help but what you posted didn't make any sense and really was
a wasted post. If your xorg.conf file was bad after installing a new driver you should have run the xorg configuration utilities. Not that your way didn't work for you. but there are better ways of doing what you did. Ubuntu has really taken to need to manually configure xorg.conf away. I would think only under certain instances ( like a specific monitor ) would you need to hand edit that file.)

---

