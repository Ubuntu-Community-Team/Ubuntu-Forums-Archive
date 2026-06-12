---
title: "CD drive not working - Xubuntu 7.10"
date: 2008-03-15
forum: General Help
---

### Post by haxx on 2008-03-15
Hey drive works last night - didnt do anything major to OS and yet it dont automount - run - burn - NODDA

i desperatly need this drive up so anything at all for ideas very appreciated


i have tried 

$ mount /cd

and get

mount: can't find /cd in /etc/fstab or /etc/mtab

---

### Post by Shazaam on 2008-03-15
That would be....
```
sudo mount /dev/yourcdrom /media/cdrom0
```
 The /yourcdrom could be hcd or hdd or scd or sdd depending on if it's IDE or SATA and one or two drives. Look in your fstab to get the correct name. /etc/fstab

---

### Post by haxx on 2008-03-15
ok i determined the cd drive label is scd0 so i entered

~$ sudo mount /dev/scd0 /media/cdrom0

and came back with ----

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type

---

### Post by haxx on 2008-03-15
in curiousity i tried a thumb drive 

it dont work either so is the problem deeper then this

---

### Post by Shazaam on 2008-03-15
Try this...
```
mount
```
and this.....
```
cat /etc/fstab
```
and post the output here.

---

### Post by haxx on 2008-03-15
i did the last two u posted and then 

~$ sudo mount /dev/scd0 /media/cdrom0


got back--

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type

still noda

---

### Post by haxx on 2008-03-15
now i get a HAL error while loging in and since i know that HAL is for auto mounting it seems its the problem

---

### Post by haxx on 2008-03-15
issue solved

i reinstalled the xfce4 thnx for the help

---

