---
title: "Boot problem after installing nvidia driver"
date: 2007-12-15
forum: General Help
---

### Post by k-i-m on 2007-12-15
HI! 
I have a HP dv 6060 with a NVIDIA Geforce GO 7200, and I have huge problems with installing the driver. Someone told me to use "envy", I did.
When I tried to reboot, I got an error! something with failed, run"fsck" manually!?!?
I did that, but then I got a new error "could not start X

I have tried:

change the xorg.conf file to a old backup I had, but I am not aloud write to the file!?
change the xorg.conf file from windows
run envy with envy -t

It seems that I can't use anything inside the /usr/bin directory.. I can't even start vim!!!
any suggestions???? 

pleeeeease help me, im sick of windows

---

### Post by taurus on 2007-12-15
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
When you are done, reboot with

```
shutdown -r now
```

---

