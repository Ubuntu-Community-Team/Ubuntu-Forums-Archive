---
title: "X Startup Failure"
date: 2007-05-08
forum: General Help
---

### Post by Warning on 2007-05-08
Hi there,

Im having an issue with ubuntu, i was trying to get the dual screen working, and i guess being a newbie and trying to do something like this is a no no :/

it says that theres an issue and gives me the option of viewing the details so i do and it says among other things the following:

```

(EE) /usr/lib/xorg/modules/extensions/libglx.so is an unrecongnized module type
(EE) failed to load module "glx" (unknown module type,  6 )
(EE) /usr/lib/xorg/modules/drivers/nvidia_drv.so is and unrecognized module type 
(EE) Failed to load module "nvidia" (unknown module type,  6 )
(EE) No Drivers

Fatal server error:
no screens found

```

Thanks for any help at all

---

### Post by Scheater5 on 2007-05-08
Alright, before messing around in x.org, make a backup copy.  
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now then, about fixing this problem.  Perhaps the easiest way to get a working system again is to boot into the live cd, and, assuming this gives you a working environment, copy the file /etc/X11/xorg.conf over the corresponding file on your Ubuntu partition.  
If you want to repair the xorg you have now, someone else will have to do that.

---

### Post by Warning on 2007-05-08
thanks for your help i managed to get hold of my friend who helped me and suggested i do this

```
sudo dpkg-reconfigure xserver-xorg
```

which fixed my issue

---

### Post by Scheater5 on 2007-05-09
Glad to hear it.  There is little more frustrating than having X break on you.  I feel your pain, and I hope you get dual monitors working.  Best of luck

---

