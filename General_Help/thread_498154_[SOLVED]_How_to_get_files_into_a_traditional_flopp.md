---
title: "[SOLVED] How to get files into a traditional floppy image (.img)?"
date: 2007-07-11
forum: General Help
---

### Post by sab0403 on 2007-07-11
Hi... didn't know exactly where to put it, so I went in here :popcorn:

Anyway, I have some files I want to use into VMWare. Since I don't have shared folders (which btw I don't know how to activate) and the VM is DOS, my only medium would be floppies. However I don't have a floppy drive, so I thought I would create a floppy image (.img). Problem is, I only know how to create images from actual floppies (with dd) and I already tried to```
dd if=$myfile of=$image.img
```but the .img file it generates doesn't conform with the standard floppy image (which was kinda to be expected... I'm not actually using a floppy). So... how do I do this?

Thanks in advance.

---

### Post by sab0403 on 2007-07-11
*bump*

---

### Post by sab0403 on 2007-07-11
Hmm... anybody?

---

### Post by smoker on 2007-07-11
hi, i dont know if this will be any good to you, and i haven't tried myself, so this is not a reccommendation, just a suggestion:
[http://www.nu2.nu/bfi/](http://www.nu2.nu/bfi/)

there may also be something here that may help, though you may have to spend a bit of time searching:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

best of luck

---

### Post by sab0403 on 2007-07-12
BFI is the ticket. CLI and GNU license, great!!

Thanks a lot! Marking it as solved...

---

### Post by sab0403 on 2007-07-12
Hmmm... no GNU license... it's actually their own license... :(

Oh well, at least it's free. :popcorn:

---

### Post by pmg on 2007-07-13
If you are using vmware, can't you just point the floppy at a file and have vmware create it, and then format it and copy files to it from the vmware guest?  Another approach would be to make a copy of diskette image file you have and point at that, and write to it from the vmware guest.  

If you want to create a diskette image without vmware you could create a FAT formatted filesystem in a file with: ```
mkdosfs -C /tmp/floppy.img 1440
```  The -C tells it to create the filesystem in a file rather then a device, /tmp/floppy.img is any filename, and 1440 is the size in 1K blocks.  

At that point you'll have a image of a empty FAT formatted floppy.  I suppose you'll want to put something on it.  :-)  To mount it as a filesystem using the loopback device:
```
mkdir /tmp/dos
sudo mount -t msdos -o loop=/dev/loop0,blocksize=1024 /tmp/floppy.img /tmp/dos
```
and then you'll be able to cd to /tmp/dos, copy files into it, etc..  When your done, make sure you cd out of that directory and **umount /tmp/dos**

---

