---
title: "I no longer have permission to access my HDD"
date: 2013-12-02
forum: General Help
---

### Post by Jason.e.kemp on 2013-12-02
A few weeks ago I switched to Ubuntu 13.10, I backed up all of my data from my windows 7 x32 on a second 2.5" hdd, transferred it all back on after i switched and removed the drive.  fast forward to now, it wasn't for me and went back to windows.  well now my back up drive only registers 6 gigs (funny because it's a 120 gig drive).  so i booted from a 13.10 disk and there was my drive even labeled "back up".  but now i'm not aloud to access my years worth of work, pictures, and music.  would someone please tell me why?

---

### Post by coffeecat on 2013-12-02
Permissions problems with saved files are usually seen with Linux filesystems, but from what you say it sounds as though your 2.5" drive might be formatted with a Windows filesystem. Unless by "backed up all of my data from my windows 7 x32 on a second 2.5" hdd, transferred it all back on after i switched and removed the drive" you were doing all this from Ubuntu in which case I think I can see what the problem is. But let's get some more information before doing any more guesswork.

Boot up with the Ubuntu 13.10 disk to the live desktop, plug the 2.5" drive in, wait until the external drive is automounted and a file manager window opens and then post the output of these two terminal commands:

```
sudo fdisk -lu
mount
```

Your can copy and paste the terminal output by highlighting it with the mouse, right-clicking and selecting copy.

---

### Post by Jason.e.kemp on 2013-12-02
maybe i did play around with format now that i think about it.  i'll do that and get back to you

---

### Post by Jason.e.kemp on 2013-12-09
the part im trying to access is a linux format.

---

### Post by coffeecat on 2013-12-10
> **Jason.e.kemp said:**
> the part im trying to access is a linux format.

Please post the output I requested in post #2.

---

