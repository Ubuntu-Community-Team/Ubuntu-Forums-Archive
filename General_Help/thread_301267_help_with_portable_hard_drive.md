---
title: "help with portable hard drive"
date: 2006-11-16
forum: General Help
---

### Post by moondogie on 2006-11-16
The portable hd is coneccted via usb .
I am running Ububtu 6.10
I am not able to drag files to the portable hd .
the error message i get is :error while copying to /media/usbdisk.](*,) 
you do not have permission .
Question : How do I get permission ?
The drive is recognized and I can drag files from it to my hd but I can't put anything on it .
Thanks, Moondogie

---

### Post by Joe_CoT on 2006-11-16
What's the filesystem of the drive? Give me this output:
```
sudo fdisk -l
```

For the most part, usb hard drives are mounted with read/write permissions. Your hard drive might have a filesystem (ex NTFS) which linux doesn't have write support for by default.

---

