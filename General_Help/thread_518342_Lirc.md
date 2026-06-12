---
title: "Lirc"
date: 2007-08-05
forum: General Help
---

### Post by Xzenome on 2007-08-05
I've just compiled and installed LIRC (I hope) and successfully modprobe'd it so the kernel module is loaded. But when I try to use *mode2* or even *sudo mode2*, I get the following error
```
mode2: error opening /dev/lirc
mode2: No such device
```

Yet when I do *ls -l /dev/lirc**, I get this:
```
crw-rw-rw- 1 root root 61, 0 2007-08-06 00:15 /dev/lirc
srw-r--r-- 1 root root     0 2007-08-06 00:17 /dev/lircd
prw-r--r-- 1 root root     0 2007-08-06 00:15 /dev/lircm
```

So either mode2 or ls is lying to me. Does anyone have any idea how I can rectify this problem? Any help will is welcome.

EDIT, if it matters, I have both lirc and lirc-x installed from the Ubuntu repositories as well as the kernel module I personally compiled.

EDIT 2, I also tried the following:
```
michael@Xenon:/usr/src/lirc-0.8.2$ sudo lircd --nodaemon
lircd: lircd(hauppauge) ready

```

Then I tried *irkick* and *mode2* again and I still got the same errors.

---

### Post by pointone on 2007-08-05
Try running "irw" and pressing some buttons on your remote.

---

