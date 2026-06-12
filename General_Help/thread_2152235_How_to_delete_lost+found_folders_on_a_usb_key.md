---
title: "How to delete lost+found folders on a usb key"
date: 2013-06-07
forum: General Help
---

### Post by seulava on 2013-06-07
Hello
I know a lot of treads exist about lost+found folders but I did not found what I need.
I'v incidentally deleted the partition from my usb. Now I have that folder lost+found and I can not delete it. 
There's nothing on my usb (so Ill not need to recover anything from that usb, so lost+found is inutil), and I need it for creat a bootable key, so I need it to be empty. 
I tried:

dd if=/dev/zero of=/dev/my_usb bs=512 
I got : Permission denied

Pleise, Help !

Thanks

Seulava

---

### Post by greatsirkain on 2013-06-07
format it in gparted

---

### Post by seulava on 2013-06-07
it's not recognized in gparted.

---

### Post by greatsirkain on 2013-06-09
try opening gparted disconnect the drive, reconnect it then refresh gparted, never had a USB that it didn't recognise, maybe faulty? Can you see it in the disk manager?
If it has a file on it then there must be a partition?

---

### Post by C.S.Cameron on 2013-06-09
Have you tried **sudo** dd if=/dev/zero of=/dev/my_usb bs=512

---

### Post by greatsirkain on 2013-07-03
just been having the same sort of problem, with a 16gb sd card, & no matter how many times I formatted it or took ownership of it I couldnt change the read/write options or remove the file :S
did you get any further forward?

---

