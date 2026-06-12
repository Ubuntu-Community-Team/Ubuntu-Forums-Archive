---
title: "Reinstall nvidia every boot?"
date: 2006-12-04
forum: General Help
---

### Post by Antimatter3009 on 2006-12-04
I'm using a driver I got off of the nVidia site and it works great, except that every time I reboot my computer I have to reinstall the driver. I've had no problems with it other than this, but when I reboot I get the blue "X won't start" screen, then go to a console, run "sh NV...", then restart gdm and it's fine, and it always works till I reboot. Anyone know what could cause this? Thanks.

---

### Post by evilghost on 2006-12-04
Run from terminal:
```

dpkg -l|grep -i nvidia

```

If you have any nvidia packages installed you need to remove them.  The installation package (.run) from Nvidia will rmmod the current module, build the new one, create the necessary symlinks in /usr/lib, and insmod the nvidia module.  Sounds like you have some left-overs from the nvidia packages.

/var/log/Xorg.0.log would tell you for sure next time X crashes but I bet you've got some linux-restricted-modules + nvidia-kernel-common.

---

### Post by suhaib on 2007-03-09
Silly me.  I shoudln't of installed the other packages through apt.  The resolution worked for me, thanks!

---

