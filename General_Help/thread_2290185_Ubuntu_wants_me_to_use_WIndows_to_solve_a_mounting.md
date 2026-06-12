---
title: "Ubuntu wants me to use WIndows to solve a mounting problem."
date: 2015-08-10
forum: General Help
---

### Post by Evil Wayz on 2015-08-10
I have encountered this issue before, but I always had a Windows computer.  This is a fairly large hard drive that I backed up my WIndows laptop with. Now the Windows laptop is dead and i need the info on the portable to restore it but as you can see, I can't access the portable.  Is there some way I can forcibly mount it or correct whatever error Ubuntu doesn't like manually?  Thanks. 
[IMG]http://i58.tinypic.com/15miogj.jpg[/IMG]

Oh, and using gparted to scan the drive and fix errors fails.

---

### Post by dino99 on 2015-08-10
first you need to be sure about that ntfs partition quality
[http://askubuntu.com/questions/47700/fix-corrupt-ntfs-partition-without-windows](http://askubuntu.com/questions/47700/fix-corrupt-ntfs-partition-without-windows)

then if it was not a borked partition, try to mount that partition with less parameters into /etc/fstab

---

