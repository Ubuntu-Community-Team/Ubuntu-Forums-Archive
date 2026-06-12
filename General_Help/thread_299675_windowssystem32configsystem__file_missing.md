---
title: "\windows\system32\config\system  file missing???"
date: 2006-11-14
forum: General Help
---

### Post by krotaz on 2006-11-14
Hi there, I've been using linux since about 4 years and I've found my self with this problem and I don't know what could be happening.

WEll, I've an AMD pc with 3 hd 2 ides and 1 sata, on the sata I've my ubuntu 6.06 and my win XP. on the ides mp3 and stuff.

Actually my mp3 are on /dev/hda1, my data and stuff of windows are on /dev/hdb1, /dev/hdc is the dvd and /dev/sda1 has the windows os and /dev/sda6 hast the linux. When I installed the ubuntu the grub was installed in /dev/hda.

The problem I have is that last friday when I tried to boot to windows an error message appear saying that windows can't load because \windows\system32\config\system  file was missing, and due to my windows was really bad I decided to reinstall. I reinstall windows and everithing was ok, today when I try to load windows the same error apears and I'm starting to think that it's not a windows problem but a grub one.

I belive grub isn't directing partitions correctly.

here's my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/hda1       /media/mp3      ext3    defaults        0       2
/dev/sda1       /media/win_os   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/windata  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and heres is the windows part of my grub file

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
map		(hd0) (hd2)
map		(hd2) (hd0)
rootnoverify		(hd2,0)
savedefault
makeactive
chainloader	+1

hope you can help me 

Thanks

---

### Post by SoggyCornflake on 2006-11-14
I had that happen to two different Computers running Windows XP - Linux wasn't istalled on either one.  

Today both computers are running Linux (One with Ubuntu) Windows machines no longer.

In your case it may be a Grub issue, but in my case I suspect some viral program corrupted the system file.

---

### Post by krotaz on 2006-11-14
I've tried to unplug the ide disks and try to boot with the sata disk only and the screen just stays in black!!   ](*,) 

Any ideas???

---

### Post by krotaz on 2006-11-15
well I just install grub on the sata disk, halt, unplug the ide disks, boot, and then the grub was there but no booting niether linux nor windows. Then I simply plug the ide disks againt an voila everithing worked fine  :-k 

Still don't understand what happend.

---

