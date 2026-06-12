---
title: "Very confused about my ntfs partitions stopping to mount"
date: 2007-09-23
forum: General Help
---

### Post by ilithanos on 2007-09-23
I got alot confused here, my fstab file has worked so far with no problems, but suddently today my ubuntu started not to mount my ntfs partitions. i havn't changed my fstab at all...

here is my fstab

[INDENT][I][COLOR="DarkOliveGreen"]proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=2acaa8e7-d008-4f26-9db9-d55573e4f62e / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=EEC87D74C87D3BC1 /media/sda1 ntfs-3g defaults,locale=da_DK.UTF-8 0 1
# Entry for /dev/sdb1 :
UUID=B80027CB00278F84 /media/sdb1 ntfs-3g defaults,locale=da_DK.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=3a747f0e-4ee9-4c0d-8b0f-1ed3d1fce6c6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR][/I][/INDENT]

I really got no idea at all on what is wrong here. so any help is appresiated.

---

### Post by MegaSvensk on 2007-09-23
Did Windows crash the last time you used it? If so, I think you have to boot up Windows once to be able use the drives in Linux. The same thing happened to me a few days ago.

---

### Post by ilithanos on 2007-09-24
thanks alot. problem solved.

---

