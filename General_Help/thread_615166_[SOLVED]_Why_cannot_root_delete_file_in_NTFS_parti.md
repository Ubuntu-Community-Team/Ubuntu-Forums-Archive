---
title: "[SOLVED] Why cannot root delete file in NTFS partition?"
date: 2007-11-16
forum: General Help
---

### Post by henry0712 on 2007-11-16
I forget the XP administrator's login password. It was said that may be useful to delete the file %systemroot%\system32\config\sam. So, I logined ubuntu and change to root user, trying to delete the file. To my surprise, I CANNOT do it!

```

root@henrydesktop:/mnt/winc/WINDOWS/system32/config# pwd
/mnt/winc/WINDOWS/system32/config
root@henrydesktop:/mnt/winc/WINDOWS/system32/config# ls -l SAM
-r-------- 1 root root 262144 2007-10-28 08:22 SAM
root@henrydesktop:/mnt/winc/WINDOWS/system32/config# rm SAM
rm: can not remove &#8216;SAM&#8217;: Read-only file system
root@henrydesktop:/mnt/winc/WINDOWS/system32/config# chmod 700 SAM
chmod: SAM: Read-only file system
root@henrydesktop:/mnt/winc/WINDOWS/system32/config# ls -l SAM
-r-------- 1 root root 262144 2007-10-28 08:22 SAM

```

How weird! 
Is there any way to manipulate the file in the NTFS partition from ubuntu? 
thanks!

---

### Post by kefurd06 on 2007-11-16
i read somewhere that linux reads ntfs partitions but will not modify them in any way. this includes saving modified files, deleting files, etc.

---

### Post by taurus on 2007-11-16
Which release are you running?  Also, how do you mount your ntfs?  If you want to write (or delete) to it, you need to mount it with ntfs-3g driver.

---

### Post by henry0712 on 2007-11-16
> **taurus said:**
> Which release are you running?  Also, how do you mount your ntfs?  If you want to write (or delete) to it, you need to mount it with ntfs-3g driver.

How to mount it with ntfs-3g?

OS's Ubuntu 6.10
$ sudo mount -t ntfs /dev/hda1 /mnt/winc

---

### Post by taurus on 2007-11-16
See if you can install ntfs-3g with

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
If everything is installed fine, then unmount it and remount it again with ntfs-3g driver.

```
sudo umount /dev/hda1
sudo mount -t ntfs-3g /dev/hda1 /mnt/winc
ls -la /mnt/winc
```

---

### Post by henry0712 on 2007-11-16
Thank Taurus! nfts-3g works well:)

---

