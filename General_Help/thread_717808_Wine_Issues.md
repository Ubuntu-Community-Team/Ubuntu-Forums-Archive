---
title: "Wine Issues"
date: 2008-03-07
forum: General Help
---

### Post by ac3raven on 2008-03-07
[[IMG]http://img111.imageshack.us/img111/2676/hl2errordv1.th.png[/IMG]](http://img111.imageshack.us/my.php?image=hl2errordv1.png)

I'm trying to install Half-Life 2, and this happens after disk 1.  I try to eject the disc and put disc 2 in, but I get that error.

---

### Post by Oldsoldier2003 on 2008-03-07
> **ac3raven said:**
> [[IMG]http://img111.imageshack.us/img111/2676/hl2errordv1.th.png[/IMG]](http://img111.imageshack.us/my.php?image=hl2errordv1.png)

I'm trying to install Half-Life 2, and this happens after disk 1.  I try to eject the disc and put disc 2 in, but I get that error.
```

wine eject :x
```
where x is the drive assigned to your cd by wine

better yet install this way:
```
wine /media/cdrom/setup.exe
```


a good link for wine and games: 
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by ac3raven on 2008-03-07
wine eject :d is not working

---

### Post by justin whitaker on 2008-03-07
There are two other potential ways of doing this. 

1. You can dump all of the disks to a directory, and install from there. That usually works.
2. Install Steam, and download the installation from there.

---

