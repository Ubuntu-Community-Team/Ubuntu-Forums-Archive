---
title: "installed with wubi 7.10 rev377 , and can't see my e: drive"
date: 2007-10-29
forum: General Help
---

### Post by ronenmv on 2007-10-29
I have  c: , e:  drives (2 partition same hard drive, win xp on c:)
I have installed with wubi 7.10 rev 377  on e: , after reboot when trying to run ubuntu I got "error 17 :  file not found"
so I modifed the menu.lst file to use hd0 and not hd1 as it was.
now ubuntu loads fine - but I can't access my e: ntfs drive, ubuntu doesn't show that partition at all - like it dos'nt exsist (but i can access c: drive)

why is that?, can I fix it ?

please help, thank you.

---

### Post by ago on 2007-10-29
The partition hosting wubi should be available as /host
The other partitions should be available as /media/XYZ 
Wubi 381 should not require any editing of menu.lst

---

### Post by ronenmv on 2007-10-29
ok, I found it under "file system/host",
it wasn't like that in wubi 7.04, in 7.04 e: was shown as host just like any other partition/drive (not under "file system")

thank you!!!

---

### Post by ago on 2007-10-29
> **ronenmv said:**
> ok, I found it under "file system/host",
it wasn't like that in wubi 7.04, in 7.04 e: was shown as host just like any other partition/drive (not under "file system")

thank you!!!

If you want the same behaviour, create /media/host, and then add an entry to /etc/fstab which binds /host to /media/host

I may add that by default in future versions.

---

