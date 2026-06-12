---
title: "Unable to restrict access to Windows drive in Hardy"
date: 2008-04-26
forum: General Help
---

### Post by Pyriel on 2008-04-26
I've just upgraded from Gutsy to Hardy, but the upgrade has left me with a problem.  I run a dual boot system and I want it set up so that I'm the only user with access to the files on the NTFS drive.  To accomplish this in Gutsy I had the following line in my fstab:
> /dev/sda1  /mnt/windows  ntfs-3g  nouser,uid=1000,gid=1000,umask=0007,locale=en_US.utf8   0    0

In Gutsy this worked just fine.  I was set as the owner, it was assigned to my group, and the umask gave the owner and group full control while giving other users none.

Since upgrading to Hardy, I've found that all users on my system have full control on the NTFS drive.  The line is still in my fstab.  Even if you right click on /mnt/windows/ and go to properties -> permissions it still shows me as the owner and group with full control while others are set to none.  In spite of this, any user can open, create, edit and delete any file on the drive.

I've tried changing the umask value to set different permissions, but no matter what I set it to, all users have full control.  I don't really understand what would cause this behaviour.  I hope someone can help me get this corrected.  Is there something in the fstab line that I need to change to get the permissions working correctly in Hardy?  Is there something elsewhere in the OS that I need to change?  Any help would be greatly appreciated.

---

### Post by Pyriel on 2008-04-29
I finally gave in and reinstalled.  After the initial upgrade I began noticing little things that weren't quite right (not the least of which is this freaking permissions problem).  So I reformatted my Linux drive and installed Hardy fresh.  I figured this would cure all my woes with the upgrade.  It did fix most of the things that I noticed, **but I still can't restrict access to my NTFS drive!**  I am completely stumped.  I even tried a more simplified fstab line.  Here is my entire fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8f06663d-3107-402f-92b8-b758ee8c0f4d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=1bd7f3da-8f39-4ede-a54c-d26f7d141f02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /mnt/windows ntfs uid=1000,gid=1000,umask=007 0 0
```

Properties still shows the correct permissions, with me as owner, my group with read and write access, and other users with no access.  Yet any user I log in as can read and write to the drive.

I'm sure there are others dual booting Hardy and XP/Vista.  Are any of you having similar issues, or is it just me?  Am I doing something wrong?  Did Hardy change the way Ubuntu handles NTFS partitions?  Or is this just some horrible bug?  I just don't understand how the OS can see the permissions I have set and yet completely disregard them.  I'm banging my head against the wall trying to make this work, so I really hope someone out there can provide me with some insight.

---

### Post by Pyriel on 2008-04-30
Well, I found the cause of my problem.  There is a bug with the 2.6.24 FUSE kernel module. ([Link]("http://http://article.gmane.org/gmane.comp.file-systems.fuse.devel/5789"))

Hopefully the Ubuntu devs will get this thing patched soon.

---

