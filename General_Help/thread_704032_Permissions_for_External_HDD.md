---
title: "Permissions for External HDD"
date: 2008-02-21
forum: General Help
---

### Post by EvMan4ca on 2008-02-21
Hello everyone,

I have an external hard drive which was originally formatted NTFS because I was primarily running Windows XP. I use it to store videos, music, and other misc files. However, when I made the switch to Ubuntu I was not able to set my permissions on the drive to read _and_ write. I've gone through the properties and tried it that way and I was wondering if:
A) I'm should just move all my files, reformat and move the files back to the external HDD or
B) if there was some way to change the permissions as root through the terminal.

Any help is appreciated. Thanks in advance!
EJM

---

### Post by spiderbatdad on 2008-02-22
While the disk is mounted you could edit /etc/fstab to umask=000  I'm not sure this would hold in the case of removable media. There is a program called Disk Manager in synaptic that will allow you to set read write permissions to mounted storage devices.

---

### Post by bodhi.zazen on 2008-02-22
Close. You should take a look at ntfs-config ;)

If you want to do it manually, you need the ntfs-3g driver. You set ownership and permissions at the time of mount or in fstab.

mount -t ntfs-3g /dev/sdxx /media/mount_point -o uid=1000,gid=100,umask=007

use those options in fstab as well

---

### Post by spiderbatdad on 2008-02-22
I never seem to get mounting right...I'm taking a screenshot of this page now.

---

