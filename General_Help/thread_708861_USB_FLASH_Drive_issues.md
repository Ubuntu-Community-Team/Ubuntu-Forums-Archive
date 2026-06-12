---
title: "USB FLASH Drive issues"
date: 2008-02-26
forum: General Help
---

### Post by decker on 2008-02-26
So i have two usb flash drives, 1gb(generic) and a 4gb(cruzer). They both report bogus free space even if they are empty. Has anyone else seen this issue before?
On the 4gb cruzer, i get this
/dev/sdb1             3.9G  3.5G  348M  92% /media/disk
but when i run "du -ch", i only get 
1.3G    total used.

So there's alot of missing space. If i fire it up in winXP, i get 2.78GB free. But linux reports 348M free.

I get similar issues with the 1gb stick.

my fstab shows
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

---

### Post by dcstar on 2008-02-27
> **decker said:**
> So i have two usb flash drives, 1gb(generic) and a 4gb(cruzer). They both report bogus free space even if they are empty. Has anyone else seen this issue before?
On the 4gb cruzer, i get this
/dev/sdb1             3.9G  3.5G  348M  92% /media/disk
but when i run "du -ch", i only get 
1.3G    total used.

So there's alot of missing space. If i fire it up in winXP, i get 2.78GB free. But linux reports 348M free.
........

There are two things that du can report - actual bytes used in the files or actual bytes that is taken up in the filesystem - and Windows may not be counting files in the "Trash" where Linux will.

---

