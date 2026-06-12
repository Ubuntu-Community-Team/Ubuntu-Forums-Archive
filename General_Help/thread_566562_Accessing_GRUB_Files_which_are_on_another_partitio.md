---
title: "Accessing GRUB Files which are on another partition"
date: 2007-10-03
forum: General Help
---

### Post by DylanNIRVANA on 2007-10-03
Hello,

My GRUB menu.lst file has messed up and i need to access the files to edit it, My Linux Mint partition holds the GRUB files somewhere (hd1,9) and i can't even boot into Linux Mint because i get the initramfs error.
So, i was wondering, while my Ubuntu partition is still bootable, if i could access the GRUB files on it and change them from there?

How can i do this?

---

### Post by kellemes on 2007-10-03
You could use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix this..

---

### Post by logos34 on 2007-10-03
Mount the linuxmint partition and go to /boot/grub/menu.lst

---

### Post by oldos2er on 2007-10-03
Try this program: [http://www.softpedia.com/reviews/linux/QGRUBEditor-Review-66577.shtml](http://www.softpedia.com/reviews/linux/QGRUBEditor-Review-66577.shtml)

 It can edit grub files on any mounted disk partition.

---

### Post by DylanNIRVANA on 2007-10-04
M'kay.

Thanks for your replies, i fixed the linux mint booting part and its all working, but i need to know how i can boot into my edUbuntu installation which is on the first partition of my external hard drive.

What would i put for the "root (???,?)" command if the OS is on "/dev/sda" ?

Please reply.

---

### Post by logos34 on 2007-10-04
try** (hd1,0)**

---

### Post by louieb on 2007-10-04
look in /boot/grub/device.map. Its a translation table.
```
(hd0)    /dev/sda
(hd1)    /dev/sdb 
```Never tried putting Linux on my external. If it doesn't have an entry you might try adding one. Don't know if it will boot but it should not mess up your other boot entries.

---

### Post by DylanNIRVANA on 2007-10-05
I fixed it. :P

---

