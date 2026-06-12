---
title: "Writing to my Windows NTFS partition from Fiesty"
date: 2007-05-31
forum: General Help
---

### Post by Rebajas on 2007-05-31
I've just installed Fiesty on a friends laptop - he wanted to keep his Windows install as well so it sits nicely on a separate partition virtually unused.

Problem is, when he does want to use it he has to transfer documents so he can use them and I have noticed that the mounted partition on the desktop isn't writable. I can view the files but I really need to make the partition writable in Ubuntu for easy document management.

The other option I thought of was to create another partition and make that accessible to bother OS's - would this be a better option altogether? And can someone point me to the best way to do this.


Cheers.


Tony.

---

### Post by renzokuken on 2007-05-31
a shared partition is a reliable way of doing it, it would have to be formatted as FAT32 though (windows and linux can both read write FAT32)

the newer and better way is to use ntfs-3g, which allows full read write of NTFS partitions.

make sure all repos are enabled, then run

```
sudo apt-get install ntfs-config
```to install it,

then run```
gksu ntfs-config
```

to automatically mount and configure any ntfs drives for read/write

---

### Post by ddeacon93 on 2007-05-31
This worked perfectly. Thanks for the info mate.

---

### Post by ondro69 on 2007-06-01
You guys are awesome!! I had the same problem and followed your advice and it worked like magic! thanks a lot man.

Ondro

---

### Post by Rebajas on 2007-06-06
Thanks, I'll give this a go next time I see my friend.

:)

---

