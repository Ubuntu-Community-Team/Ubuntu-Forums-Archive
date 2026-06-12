---
title: "Gnombaker Problem"
date: 2005-08-07
forum: General Help
---

### Post by rogeriovinhal on 2005-08-07
I installed GnomeBaker CVS, but i have a problem that does not seem too hard to solve.

When I try to burn a CD, GnomeBaker says it can't unmount /media/cdrom1, because ir is not mounted, and it doesn't do a thing.

But i really think it IS mounted, because it even shows an icon of the CD on the desktop. And the "Computer" shows a "Blank CD" instead of the Device, so, I presume it is mounted.

---

### Post by rogeriovinhal on 2005-08-08
Up

---

### Post by wellery on 2005-08-08
type this to view mounted devices on the console:

```
mount
```

---

### Post by rogeriovinhal on 2005-08-08
In fact, it doesn't show itself in the "mount" command, and if I try to mount it, it complains about the FS.

How then GnomeBaker expect the Blank CD to be mounted? Shouldn't it mount by itself?

---

### Post by wellery on 2005-08-08
Yes, when you insert a blank cd it should mount itself.

---

### Post by rogeriovinhal on 2005-08-09
But it seems mounted. I can grab files and put in it so Nautilus can burn the CD. Actually, Nautilus is the only way I coulf find to burn CDs, but I want a better interface like gnomeBaker.

---

### Post by aloysius on 2005-08-11
[QUOTE=rogeriovinhal]But it seems mounted. I can grab files and put in it so Nautilus can burn the CD. Actually, Nautilus is the only way I coulf find to burn CDs, but I want a better interface like gnomeBaker.[/QUOTE]
 I am having exactly the same problem and have been unable to work out why...

---

### Post by aloysius on 2005-08-14
[QUOTE=aloysius]I am having exactly the same problem and have been unable to work out why...[/QUOTE]
 i have solved my problem at least by fixing the fstab file...it was mounting cdrom to /dev/hdd instead of hdc which is what i needed for my system...check that yours is set up properly...mine working fine now...

---

