---
title: "Mount in more than one place?"
date: 2006-10-25
forum: General Help
---

### Post by darundal on 2006-10-25
Hi, I was wondering if it is possible to have one drive (specifically, one partition of the same drive) mounted in multiple places...thanks.

---

### Post by pay on 2006-10-25
If you mean just a shortcut to it then just copy the drive and paste it to the new directory. 
It will still be mounted in the old place but it will have a shortcut in the new place.

---

### Post by CatKiller on 2006-10-25
> **darundal said:**
> Hi, I was wondering if it is possible to have one drive (specifically, one partition of the same drive) mounted in multiple places...thanks.

Yes, it's possible. The easiest way isn't to do what you've asked, but to have a symbolic link from where you want the mounted partition to where it's actually mounted. I would strongly recommend this.

If you really really really want to mount the same filesystem twice, you can use the bind option for the mount command. From **man mount**:>        Since Linux 2.4.0 it is possible to remount part of the file  hierarchy
       somewhere else. The call is
              **mount --bind olddir newdir**
       After this call the same contents is accessible in two places.  One can
       also remount a single file (on a single file).


---

