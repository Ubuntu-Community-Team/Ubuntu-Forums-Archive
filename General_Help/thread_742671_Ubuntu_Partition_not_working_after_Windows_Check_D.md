---
title: "Ubuntu Partition not working after Windows Check Disk"
date: 2008-04-01
forum: General Help
---

### Post by BoUgS on 2008-04-01
Hi-

I setup a dual boot with windows xp and the latest version of ubuntu.  i had some initial trouble getting the graphics drivers working but thats fine now.  every time i would boot up the windows partition after i installed ubuntu it would try to do a checkdisk.  i finally missed cancelling it today and after it finished i tried going back into ubuntu and the gui wouldnt load.  i would see the ubuntu loading bar finish and then the screen would go black.

things to note:

* i can successfully enter recovery mode
* i ran fsck from a live disk and the partition is clean

* i installed [Ext2 Installable File System For Windows]("http://www.fs-driver.org/index.html") before this incident and was able to browse my linux partiton in windows.  when i click on the drive now i get a pop up saying "This drive is not formatted.  Would you like to format it now?"

* while chkdsk was running it reported no errors but when it was done it did spit out a bunch of stuff but the screen changed to windows loading quickly so i was unable to read what it said.

System:

Dell E1505
Intel Core Duo
2 GB RAM
Windows XP SP2
Ubuntu 7.10

if i posted this in the wrong sub forum please let me know and i will pm the mods to move it.

Thanks in Advance
Bougs

---

### Post by zvacet on 2008-04-02
In recovery mode type

```
startx
```

or

```
/etc/init.d/gdm start
```

---

### Post by BoUgS on 2008-04-02
> **zvacet said:**
> In recovery mode type

```
startx
```

or

```
/etc/init.d/gdm start
```

it does the same thing as when i boot up normally.  the screen goes black and the back light turns on and off in like 3 sec intervals.  in the first command the backlight just stays on.

---

