---
title: "Help, GRUB is fine but linux wont boot :("
date: 2007-09-17
forum: General Help
---

### Post by Ivanodeville on 2007-09-17
Well i´ve got 2 partitions, one for windows and one for linux, I resized them with paragon partition manager resize util. to get more space on linux partition and it dit well. Now when mi pc starts the grub starts well and if a choose to boot win it boots perfectly but if I boot linux after the second boot screen (loading...) it gets all black and nothing happens...
I searched but all found is grub recuperation and i think the grub is OK.

Any ideas ?

---

### Post by jamvegan on 2007-09-17
I think that if you moved the start of your linux partition, that could mess up the hexadecimal location string in grub.  Try entering edit mode when the grub menu comes up (type "e" with the Ubuntu entry highlighted).  Change the kernel line so that instead of looking something like this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1 ro quiet splash
```
it looks something like this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/hda2 ro quiet splash
```
where you use the actual drive/partition id of your Ubuntu partition, of course. :-)  Then type "b" to boot.  If this works then you can make the change permanent in /boot/grub/menu.lst.

Hope this helps!

---

### Post by Ivanodeville on 2007-09-17
oh thank you very much, ill try it when i get home

gracias !!

---

