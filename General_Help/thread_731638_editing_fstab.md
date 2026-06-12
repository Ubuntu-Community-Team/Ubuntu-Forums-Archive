---
title: "editing fstab"
date: 2008-03-22
forum: General Help
---

### Post by jprebechi on 2008-03-22
Hi all.

First of all, i'll explain my situacion.

i've got 2 differents hard disks. one which had ubuntu and windows, plus an ntfs partition (a) for different files, and the other disk was just 1 partition (b) (ntfs) with personal things.

when i switched to ubuntu, and deleted windows, i transformed the partition b, from ntfs to ext3, but it wasn't recognized.

so i followed a guide on the internet, edited fstab, and could mounted it. the problem is the following (here is my fstab file):


	# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f191e2a1-c40f-4aca-b5eb-17dd5e24d909 /               ext3    defaults,user_xattr,errors=remount-ro 0       1
# /dev/sda5
UUID=cbbd4663-1075-4c66-ad0e-083db17ff99e /home           ext3    defaults,user_xattr        0       2
# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=cf6f74de-bb49-44d6-a1d2-3bf9ac216cb0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1 /storage ext3 defaults 0 0

i just realized it.. i added the line "/dev/hda1 /storage ext3 defaults 0 0" and mounted the converted ntfs to ext3 partition in /storage, but the other line (# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1) is still there.

my question is simple, and maybe, stupid (because maybe this won't ever give me trouble, but i'm curious). can i edit my fstab without risk about dataloss? or should i look carefully anything i edit ? should i leave the file as it is? delete the "# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1" part? or replace it with the actual partition? (the ext3, with it's own uuid, etc)

Thx in advance.

jprebechi

---

### Post by forestpixie on 2008-03-22
AFAIK fstab is ther to tell the system which partitions to mount and where - you shouldn't get any dataloss, but that doesn't mean you won't, you need to be careful how you do edit it or you could end up not being able to boot properly.

I was under the impression that buntu doesn't refernce as hda anymore and uses sda for PATA and SATA drives. Maybe you should check with sudo fdisk -l and blkid

---

### Post by dcstar on 2008-03-22
> **jprebechi said:**
> Hi all.

First of all, i'll explain my situacion.

i've got 2 differents hard disks. one which had ubuntu and windows, plus an ntfs partition (a) for different files, and the other disk was just 1 partition (b) (ntfs) with personal things.

when i switched to ubuntu, and deleted windows, i transformed the partition b, from ntfs to ext3, but it wasn't recognized.

so i followed a guide on the internet, edited fstab, and could mounted it. the problem is the following (here is my fstab file):


	# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f191e2a1-c40f-4aca-b5eb-17dd5e24d909 /               ext3    defaults,user_xattr,errors=remount-ro 0       1
# /dev/sda5
UUID=cbbd4663-1075-4c66-ad0e-083db17ff99e /home           ext3    defaults,user_xattr        0       2
# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=cf6f74de-bb49-44d6-a1d2-3bf9ac216cb0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1 /storage ext3 defaults 0 0

i just realized it.. i added the line "/dev/hda1 /storage ext3 defaults 0 0" and mounted the converted ntfs to ext3 partition in /storage, but the other line (# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1) is still there.

my question is simple, and maybe, stupid (because maybe this won't ever give me trouble, but i'm curious). can i edit my fstab without risk about dataloss? or should i look carefully anything i edit ? should i leave the file as it is? delete the "# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1" part? or replace it with the actual partition? (the ext3, with it's own uuid, etc)

Thx in advance.

jprebechi

Install the **pysdm** package and use its GUI interface to do the job for you.

---

### Post by jprebechi on 2008-03-22
i installed it, and everything about the hda1 partition seems OK (it's mounted on storage, ext3, nothing wrong).

maybe i just leave it as it's now, but i don't know.. i'm too fu*** curious :P. also, i could back up my fstab file and try deleting the following lines

# /dev/hda1
UUID=3088CA5F88CA22E8 /media/hda1 ntfs defaults,umask=007,gid=46 0 1

what do you think guys?

---

