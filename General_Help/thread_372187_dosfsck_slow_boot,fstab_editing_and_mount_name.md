---
title: "dosfsck slow boot,fstab editing and mount name"
date: 2007-02-27
forum: General Help
---

### Post by plopke on 2007-02-27
ubuntu version 6.1
I'm a big noobie but configured by sniffling and power googling my way around most configuration problems but 2 things still really bug me

a) my boot up time can last as long as 4 min with something like this happening

checking ubuntu partion clean files 

dosfsck 39 files .... <- windows partion THIS takes like 3 min
dosfsck clean recovery partition

And worst thing about this is after doing this all he say everytime everything is ok

I snuffled around and found i have to edit the folowing to not mount the recovery disk and do not check the windows partition

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=799730f6-60f2-40f9-9472-683d62a0487d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9877-489A  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       ** change to zero 1**
# /dev/hda2
** DELETE THIS UUID=E425-EAC7  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0 1**
# /dev/hda4
UUID=59c7c0de-29c8-4721-bc59-c105e28bc8df none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Now the second problem that i find annoying is that my disk on the gnome desktop get the names RECOVERY for hda2 (asus recovery) but for the hda1 (windows) it gives me a disk icon with the following name _indetermi , any reason why i do get this name speciall because the recovery partion doesnt get weird name

---

