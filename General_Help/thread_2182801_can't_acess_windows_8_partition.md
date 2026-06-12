---
title: "can't acess windows 8 partition"
date: 2013-10-22
forum: General Help
---

### Post by spstharaka on 2013-10-22
I can't acess windows 8 partition.It can happen this error"    Error mounting /dev/sda5 at /media/tharakaz/10886791886773DE: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda5" "/media/tharakaz/10886791886773DE"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."..Please give me help to solve this problem.

---

### Post by whitesmith on 2013-10-22
Hi and welcome. Your post confuses me. For starters, how about booting from an Ubuntu live DVD and selecting Try. When the desktop comes up, hit Ctrl+Alt+t, then type```
sudo fdisk -l
```Post the output between code tags. This will help us get a handle on your issue.

---

### Post by spstharaka on 2013-10-22
I can't acess windows 8 partition.It can happen this error"    Error mounting /dev/sda5 at /media/tharakaz/10886791886773DE: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda5" "/media/tharakaz/10886791886773DE"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0). Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda5': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option."..Please give me help to solve this problem.

---

### Post by ajgreeny on 2013-10-22
Do you have ubuntu installed to hard disk in a dual boot with Win8?

I am also a bit confused but if you do have a dual boot system, and in view of the error comment:-
> /dev/sda5" "/media/tharakaz/10886791886773DE"' exited with non-zero  exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
I am wondering if you have properly shutdown Win8 or are using the default, which I believe is hibernation of some sort, not a total shutdown.  That could cause you all sorts of problems if you do start ubuntu when Win8 is just in hibernation and I think it is possible to corrupt your Windows installation if you don't proceed with care.

---

### Post by oldfred on 2013-10-22
Duplicate threads merged. Please do not create duplicate threads on same topic.

---

### Post by spstharaka on 2013-10-22
Thanks for a reply [**[COLOR=#000000]whitesmith[/COLOR]**]("http://ubuntuforums.org/member.php?u=664837") give me quick reply,below out put occur code (sudo fdisk -l),

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c7a859b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   157571071    78426112    7  HPFS/NTFS/exFAT
/dev/sda3       157571072   362371071   102400000    7  HPFS/NTFS/exFAT
/dev/sda4       362373118   976771071   307198977    f  W95 Ext'd (LBA)
/dev/sda5       362373120   567173119   102400000    7  HPFS/NTFS/exFAT
/dev/sda6       567175168   771975167   102400000    7  HPFS/NTFS/exFAT
/dev/sda7       771977216   889161727    58592256   83  Linux
/dev/sda8       889163776   974819327    42827776   83  Linux
/dev/sda9       974821376   976771071      974848   82  Linux swap / Solaris

---

### Post by spstharaka on 2013-10-22
Thanks for reply.soory for duplicate thread i created.i'm new to ubutu.so i confuse this problem,ubuntu installed to hard disk in a dual boot with Win8.

---

### Post by oldfred on 2013-10-23
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

