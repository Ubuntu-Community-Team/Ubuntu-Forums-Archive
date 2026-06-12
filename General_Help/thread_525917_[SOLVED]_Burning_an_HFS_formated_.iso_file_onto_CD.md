---
title: "[SOLVED] Burning an HFS formated .iso file onto CD"
date: 2007-08-14
forum: General Help
---

### Post by arsenic23 on 2007-08-14
Ok, I have a .iso file that is not of the format iso9660.  It is HFS.  I need to burn this .iso file onto CD, but it needs to remain HFS formated.  I first tried to do this on someone elses PC (windows) with no luck at all using a variety of burning applications.  When I got home I installed HFS support on my machine here and was able to mount the .iso to a folder using this command:

```
sudo mount -o loop -t hfs CD.iso ~/Desktop/tmp
```

So the image is good, it is HFS formated, ok awsome.  But how do I go about burning this thing?

---

### Post by arsenic23 on 2007-08-15
Surprisingly, while K3b only made coasters, Gnomebaker burnt the HFS cds without any special input from me.  Didn't see that coming.

---

