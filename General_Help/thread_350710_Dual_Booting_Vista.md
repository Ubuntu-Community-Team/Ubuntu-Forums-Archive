---
title: "Dual Booting Vista"
date: 2007-01-31
forum: General Help
---

### Post by shanepardue on 2007-01-31
I installed Vista then Kubuntu as is recommended and I can't seem to find the right configuration for the vista entry in grub, Here's the output of fdisk and my current grub config

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4570    36700160    6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2            4571        7640    24659775    7  HPFS/NTFS
/dev/sda3            7641        9639    16056967+  83  Linux
/dev/sda4            9640        9729      722925    5  Extended
/dev/sda5            9640        9729      722893+  82  Linux swap / Solaris

```
```
title Windows Vista
root (hd0,1)  --I've tried every partition number and even sd instead of hd
makeactive
chainloader +1

title		Kubuntu (2.6.17-10-generic)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Kubuntu (2.6.17-10-generic) Recovery Mode
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot
```

---

### Post by towsonu2003 on 2007-01-31
try:
```

title=Windows Vista
rootnoverify (hd0,1)
chainloader +1
makeactive

...

```

please let us know if that works for you -thanks :)

---

### Post by shanepardue on 2007-02-01
Unfortunately that did not work. The error message that I always get including this time is...
"error 13: Invalid or unsupported executable format"

---

### Post by towsonu2003 on 2007-02-01
ok, and what about this one:
```

title         "My Windows Vista"
root         (hd0,1)
chainloader      +1

...

```

In case you are wondering whether I'm playing around ;) I'm not. I saw the previous code a month ago in a mailing list. This one, I just found at [http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

Let's see if this one works...

---

### Post by shanepardue on 2007-02-01
I'm sorry, it doesn't work either.

I wish I didn't have to mess with windows, but my job requires me knowing windows well.

---

### Post by shanepardue on 2007-02-01
Since this computer was recently formatted, I decided to reinstall both operating systems. I'm not 
sure what happened the first install, but after this install, vista appeared on grub automatically. 
Sorry for the trouble!!

---

