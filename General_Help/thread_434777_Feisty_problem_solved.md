---
title: "Feisty problem solved"
date: 2007-05-06
forum: General Help
---

### Post by damotor on 2007-05-06
I just updated from Edgy to Feisty and when I restarted my pc spent 3 or 4 minutes, first received a 'Uniform CD-ROM direver Revision: 3.20' message and after that a 'can't access tty; job control tuerned off' message. At he end I just got a command line.
The problem was in my /boot/grub/menu.lst . I found it beacause booting from the liveCD and making 'sudo fdisk -l' I realized that Feisty names my hard disk as sda, but in menu.lst appeared hda.
The other problem is that in menu.lst appears
```
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda6 ro quiet splash
```
but the correct order is
```
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 ro quiet splash
```

I hope this may help someone.

---

