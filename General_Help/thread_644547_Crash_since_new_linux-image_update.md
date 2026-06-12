---
title: "Crash since new linux-image update"
date: 2007-12-19
forum: General Help
---

### Post by frenchy82 on 2007-12-19
Hello,

Today we had some update from gutsy like linux image.

So after we have a message to re boot the pc and then as it start there is this message

"Booting .... 2.6.22-14 generic
kernel /vmlinuz-2.6.22-14 generic
root=UUID=.....
loop=/ubuntu/disks/root.disks ro quiet splash automatic_ubiquity  locale=fr

Error 17: File not found

I must say that wubi worked very well until now.
In Windows i have "/ubuntu/disks/root.disks"

I really hope that somebody could help me (with simply words because my en glish is not so good :) )

Thanks a lot

---

### Post by huysmki on 2007-12-19
Hi,

I had the same problem and this fixed it:

1. Boot Windows.
2. edit file X:/ubuntu/disks/boot/grub/menu.lst where X is the drive letter where wubi was installed
3. change "kernel   /vmlinuz-2.6.22-14-generic ...." to "kernel /**boot/**vmlinuz-2.6.22-14-generic ...."
4. change "initrd  /initrd.img.2.6.22 ...." to "initrd  /**boot**/initrd.img.2.6.22 ...."
5. save the file
6. Reboot ubuntu

Greetz

---

### Post by frenchy82 on 2007-12-19
Hello,

I confirm it works perfectly
Ubuntu is back with your help

Many thanks

---

