---
title: "New problem mounting external drives"
date: 2014-09-14
forum: General Help
---

### Post by sbennettgso on 2014-09-14
All the sudden today external drives (cameras, thumb drives, etc.) will not mount automatically.  I can see them when I use ```
sudo fdisk -l
``` and I can mount them manually using ```
sudo mount -t ntfs /dev/sd(xy) /media
``` But particularly for cameras that's kind of a pain - I can no longer automatically start Shotwell when I plug in a camera for example.

I find it very hard to believe that all the sudden I've fried a bunch of drives, particularly since I can read from and write to them using the /media directory.

It seems like this is sort of a permissions thing, but as far as I know I haven't changed anything like that recently (I'm running 14.04 with MATE desktop).

Any ideas where I should look?

Thanks,
Scott

---

### Post by sbennettgso on 2014-09-15
Looks like a recent update broke this.  I installed the latest updates this evening and I can access thumb drives and all that again.

Thanks,
Scott

---

