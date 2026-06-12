---
title: "Hard Drive Stopped Being Listed"
date: 2008-02-08
forum: General Help
---

### Post by 360freak on 2008-02-08
Normally, my hard drive containing Windows is listed under Computer as "250 GB Volume" or something along those lines. For some reason though, it is no longer listed, and I have no idea why.  I just recently plugged in my external hard drive and set up a partition on it, but I do not know if that was a cause, or just a coinsedence. Any help is greatly appreciated, as I need this to backup my data since I'm reinstalling Windows.

---

### Post by taurus on 2008-02-08
You're supposed to safely unmount the drive first before you unplugged it in windows.  I am sure that is the problem why it wouldn't mount automatically now.  

See which device it is and try to mount it by hand to see if you'll be greeted with a message about you need to boot into windows and unmount your device cleanly first or you can use the force option to mount it.

```
sudo fdisk -l
```
_Assuming_ it is /dev/sdb1, try

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
```

---

### Post by 360freak on 2008-02-09
I get the following error message, "You do not have the permissions necessary to view the contents of "sdb1"."

---

