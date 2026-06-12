---
title: "Some problems I ran into after installing Windows XP."
date: 2007-07-02
forum: General Help
---

### Post by jms1989 on 2007-07-02
Hi, six days ago I installed Windows XP to test out some memory. It's still on my computer but I use it for games and such.

I'm having trouble with the time not staying synchronized, on will have the current time and the other will be five hours ahead or behind. A couple file system issues, Ubuntu sometimes refuses to mount the two ntfs file systems I use for windows.

I'm also have some problems that are not or somewhat related to me installing windows. KTorrent keeps giving me an error saying, "An error occurred while loading the torrent. The torrent is probably corrupt or is not a torrent file." Amorok is having trouble playing a song after the first one has been finished. I don't have any file system issues on the windows and I installed a ext3 driver to read my Linux partitions.

My current fstab file is as follows;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 	/  	        ext3    defaults,errors=remount-ro 0       0
/dev/hdb1	/media/HDD2     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb2	/media/HDD3     ext3    defaults        0       0
/dev/hda2	/media/WinXP  ntfs  nls=utf8,unmask=0222  0       0
/dev/hda5	none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0





Please help me, thanks in advanced.
jms1989.

---

### Post by jms1989 on 2007-07-04
Oh geez, what happened to all the help around here? Judging by the amount of members here, there has got to be somebody who can help. You don't have to answer all the questions in one bite. I really need this help to fix my dilemmas with WinXP and Ubuntu.

Come on now, don't be shy.

---

### Post by trak87 on 2007-07-04
The time difference is because one operating system is using Greenwich Mean Time (or "Z" for Zulu time) as the basis and the other is basing time on Greenwich Mean Time minus 5 hours, which I believe is Eastern Standard Time zone. You just need to make both operating systems use the same base time.

I don't think your /etc/fstab file has anything to do with ktorrent file corruption although you don't provide enough information to diagnose the problem.

---

### Post by louieb on 2007-07-04
The clock switching time when alternating boots between XP and Linux is a pain. To keep Linux from using UTC Right click on the clock > Preferences > uncheck the UTC box. Or if you don't have the clock edit **/etc/default/rcS** and change the line UTC=yes to UTC=no
If you need to change the timezone this can be done by runing sudo tzselect.
[Stuff that doesn't fit anywhere else]("http://louboldt.com/ilinuxmisc.htm")

---

### Post by jms1989 on 2007-07-05
KTorrent, I think is a problem in of itself.

When Amorak finishes a song, it won't continue to the next. It's trying to play from a music library on a NTFS partition managed by windows. It will play the first song but not the next.

I still have problems mounting one of the ntfs partitions, my extra ntfs partition, which is D:\ on windows and /media/HDD2 on linux, mounts ok but the other wont.

I will need to double check on the clock issue to make sure it has been resolved. I will post beck with the update.

UPDATE: The system clock issues seems to be ok. Playing mp3s seems to be a problem. I need to find the codecs for decoding the mp3s cleanly. That may be the problem with Amorak. I fixed the problem with KTorrent by deleting the config files them reopening it.

---

### Post by jms1989 on 2007-07-15
Update:
KTorrent is still acting up.

Amarok is working fine except I can't use cross-fading.

The Ubuntu system time stays the same but each time I boot to windows it's 5 hours ahead of time.

---

