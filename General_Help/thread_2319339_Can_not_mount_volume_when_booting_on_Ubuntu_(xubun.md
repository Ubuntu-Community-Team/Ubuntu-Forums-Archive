---
title: "Can not mount volume when booting on Ubuntu (xubuntu desktop interface)"
date: 2016-04-03
forum: General Help
---

### Post by Michel_Tremblay on 2016-04-03
Yesterday i was able to acces my D drive on Windows 8.1 with Ubuntu. Today i cannot do it. I have this error message.   Error mounting /dev/sda3 at /media/bluesman/5DA4E8CE1F831F9C: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/bluesman/5DA4E8CE1F831F9C"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0). Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda3': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.  I have 2 volume that refused to mount and i would like to have access to them.   What is the prodecure to make it work and keep those volume available.   Thanks for your help

---

### Post by Michel_Tremblay on 2016-04-03
After verifidation, the fast startup was enable in Windows 8.1, i removed the checkmark and now it is working, i can see the NTFS drives. What i do not understand is that it was enable yesterday.....another mystery for me to solve.

---

