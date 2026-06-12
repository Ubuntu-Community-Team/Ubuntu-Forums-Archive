---
title: "HDD's rename on reboot."
date: 2008-04-14
forum: General Help
---

### Post by Vegar on 2008-04-14
I didnt know what to search for, and i don't really now kow to explain my problem in any detailed way... its just that everytime my computer reboots, it "remounts my hdds with different names" so all the applications i use gets ******.. Because the folders I've specified doesnt exist. etc.
Pic:
[[IMG]http://img391.imageshack.us/img391/725/screenshotwv2.th.png[/IMG]](http://img391.imageshack.us/my.php?image=screenshotwv2.png)

---

### Post by drdrewdown on 2008-04-14
here you go sir

[http://ubuntuforums.org/showthread.php?t=750490]("http://ubuntuforums.org/showthread.php?t=750490")


that should fix ya if you follow this thread

cheers

---

### Post by Vegar on 2008-04-14
does this look alright, or do i "need" more options?
```

/dev/sdb1       /media/disk     auto    rw,user
/dev/sdc1       /media/AMITECH  auto    rw,user 
/dev/sdd1       /media/WD500    auto    rw,user

```

---

### Post by drdrewdown on 2008-04-14
the biggest part of this is SETTING THE UUID's per drive/mount

read the part on there about the UUID's & how to find them & how to set them up in fstab

---

