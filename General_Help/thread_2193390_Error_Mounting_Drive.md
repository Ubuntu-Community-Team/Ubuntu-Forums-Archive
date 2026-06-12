---
title: "Error Mounting Drive"
date: 2013-12-12
forum: General Help
---

### Post by godbotcc on 2013-12-12
Hi,

I'm kind of new to linux, but I'm started to get a hang of it.

I created a bootable USB, one partition has a FAT32 startup for Xubuntu.  With another partition which is NTFS which is encrypted with Truecrypt. (Krypton is the drive, Kryptonite is the encrytped file).

It was working fine yesterday, however today when I booted up Xubuntu, I tried mounting it with Truecrypt and I get an error. 

```
Error mounting /dev/sdc2 at /media/xubuntu/Krypton: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdc2" "/media/xubuntu/Krypton"' exited with non-zero exit status 21: mount: according to mtab, /dev/sdc2 is already mounted on /media/xubuntu/Krypton
```

I've been trying to look on google for a few hours how to fix it, and nothing really seemed to work (if I'm doing it correctly)

Thanks a lot, any help would be appreicated!

Mark

---

### Post by cjhabs on 2013-12-12
It says that it is already mounted. You could try unmounting it first with:
sudo umount /dev/sdc2
Then trying to mount it again.

---

