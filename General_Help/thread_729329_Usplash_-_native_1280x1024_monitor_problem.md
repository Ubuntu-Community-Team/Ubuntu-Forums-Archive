---
title: "Usplash - native 1280x1024 monitor problem"
date: 2008-03-19
forum: General Help
---

### Post by KraftSingle on 2008-03-19
The Usplash screen on both shut down and boot up are off center and tells me to set it to 1280x1024 60hz refresh rate. My monitor definitely supports 1280x1024. I find all sorts of guides for people who can't use 1280x1024 and want to lower the resolution ([http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)), but none for my situation. 

I have a HP F1703 Flat Panel Monitor.

Any help would be very much appreciated.

More Info:

```
# Usplash configuration file
xres=1280
yres=1024

```

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a237f175-f72d-4f4d-81$
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a237f175-f72d-4f4d-81$
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

```

---

### Post by KraftSingle on 2008-03-19
Ooops.

---

