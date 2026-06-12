---
title: "NTFS-3g partitions: noexec and utf8 problems"
date: 2006-11-27
forum: General Help
---

### Post by Régis B. on 2006-11-27
Hello everyone,
I've got a weird problem with the mounting of my windows partitions using ntfs-3g. For info, I'm using KUbuntu (Edgy).

Here is my /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
(...)
/dev/sda2 /media/windows_c ntfs-3g defaults,exec,auto,nls=utf8,user,suid,uid=1000,gid=1000,umask=077 0 0
/dev/sda5 /media/windows_e ntfs-3g defaults,exec,auto,nls=utf8,user,suid,uid=1000,gid=1000,umask=077 0 0


My windows partitions are, as you might have guessed, /dev/sda2 and /dev/sda5. After startup, here is the result of a "mount" command:

> 
(...)
/dev/sda2 on /media/windows_c type fuse (rw,nosuid,nodev,noexec,noatime,allow_other)
/dev/sda5 on /media/windows_e type fuse (rw,nosuid,nodev,noexec,noatime,allow_other)


/dev/sda2 and /dev/sda5 are set to "noexec", even though I used "exec" in my fstab. Incidentally, I cannot create files with utf8 characters (such as "régis".

After that, if I do 
> regis@regis-kubuntu:~$ sudo umount /media/windows_c
regis@regis-kubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/windows_c


then I get:

> 
regis@regis-kubuntu:~$ mount
(...)
/dev/sda5 on /media/windows_e type fuse (rw,nosuid,nodev,noexec,noatime,allow_other)
/dev/sda2 on /media/windows_c type fuse (rw,nosuid,nodev,noatime,allow_other)


Which is correct! Plus, I can now create a "régis" folder in /media/windows_c, which is precisely what I wanted.:-D 

The thing is, I would very much like not to have to manually unmount/remount my windows partitions after startup, so could anyone here give me a hint about my problem?

Régis B.

---

### Post by givré on 2006-11-27
ntfs-3g don't use the same option as the kernel driver.
Look at ```
man ntfs-3g
```

---

### Post by Régis B. on 2006-11-29
You were right, I should have RTFM :-D 

The right config for fstab was:

> 
# /dev/hda1
UUID=BEB03277B032366D /media/hda1     ntfs-3g    locale=en_GB.UTF-8,umask=007,gid=46 0       1
# /dev/hda2
UUID=E8504C87504C5F06 /media/hda2     ntfs-3g    locale=en_GB.UTF-8,umask=007,gid=46 0       1


Régis, happy with his accentuated file names

---

