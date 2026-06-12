---
title: "unable to write to an external USB hard drive"
date: 2007-04-23
forum: General Help
---

### Post by tesseract420 on 2007-04-23
I had this problem in Dapper and Edgy; it was never solved. Some people reported various success by modifying the fstab file; when I did so it never worked.

The drive is NTFS formatted, but in Feisty the NTFS Configuration Tool is installed and enabled for external drives; so that shouldn't be the problem.

The drive shows up as owned by root, the following command yields:

tesseract420@tesseract420:~$ sudo chmod 777 /media/"New Volume"
chmod: changing permissions of `/media/New Volume': Read-only file system

and the permissions aren't changed.

I thought that the NTFS configuration tool fixed the NTFS problem, but I can't change permissions.

This problem occurs only with USB hard drives, not with USB memory sticks. 

By the way, how do you log in as root? If you try to log in from the Ubuntu desktop initial screen, you get a message saying, "can't log in from this screen".

---

### Post by yopnono on 2007-04-23
> **tesseract420 said:**
> I had this problem in Dapper and Edgy; it was never solved. Some people reported various success by modifying the fstab file; when I did so it never worked.

The drive is NTFS formatted, but in Feisty the NTFS Configuration Tool is installed and enabled for external drives; so that shouldn't be the problem.

The drive shows up as owned by root, the following command yields:

tesseract420@tesseract420:~$ sudo chmod 777 /media/"New Volume"
chmod: changing permissions of `/media/New Volume': Read-only file system

and the permissions aren't changed.

I thought that the NTFS configuration tool fixed the NTFS problem, but I can't change permissions.

This problem occurs only with USB hard drives, not with USB memory sticks. 

By the way, how do you log in as root? If you try to log in from the Ubuntu desktop initial screen, you get a message saying, "can't log in from this screen".

You have this right.
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

You need to set a password for the root account, and also enable the root account to login. check the login manager for that, to set the password check the users and group.

---

### Post by tesseract420 on 2007-04-23
1. It doesn't seem that they've resolved the issue in the other thread. 
2. Where is the login manager? Under system-administration-login window there is no place to set these values.

But thanks.

---

