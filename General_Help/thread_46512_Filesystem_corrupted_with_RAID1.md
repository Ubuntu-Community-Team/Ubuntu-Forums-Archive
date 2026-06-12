---
title: "Filesystem corrupted with RAID1"
date: 2005-07-05
forum: General Help
---

### Post by ggnore on 2005-07-05
Hello

This system is a server including samba (domain controller / file sharing).
Last week end, the system crashed.

When i rebooted the system on monday, Bios said: 

> Sec Master Hard disk : SMART : Command Failed
F1 to resume

I push F1...

After a small boot sequence, here s what is shown on the screen for ever (it loops):

> 
hda : dma_intr : status = 0x51 { drive ready seek complete
hda : dma_intr : error = 0x40 Error }
{incorrectable error}, lba sect 302925799, high = 18, low = 935911, sector 302925799
ide : failed opcod was : unknown
end request : I/O error, dev hda, sector 302925799
[COLOR=DimGray][7 times][/COLOR]
printl : 7 messages suppressed
raid 1 : hda8 : rescheduling sector 4096 

It seems that the file system of a partition is broken.

Here is a few files that may help:
[QUOTE="/etc/fstab"]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
#/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/md0 / ext3 noatime,errors=remount-ro 0 1
/dev/md1 /usr xfs noatime 0 2
/dev/md2 /home xfs noatime,quota 0 2
/dev/md3 /partages xfs noatime,quota 0 2
/dev/md4 /var ext3 noatime 0 2
/dev/md5 /tmp ext3 noatime 0 2
/dev/hda5 none swap sw,pri=1 0 0
/dev/hdc5 none swap sw,pri=1 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/QUOTE]

[QUOTE="/etc/raidtab"]# Sample raid-1 configuration
# / en RAID1
# ==============================
raiddev /dev/md0
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda2
raid-disk 0

device /dev/hdc2
raid-disk 1

# /usr en raid
# ===============================
raiddev /dev/md1
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda3
raid-disk 0

device /dev/hdc3
raid-disk 1

# /home en raid1
# ===============================
raiddev /dev/md2
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda6
raid-disk 0

device /dev/hdc6
raid-disk 1

# /partages en raid
# ===============================
raiddev /dev/md3
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda7
raid-disk 0

device /dev/hdc7
raid-disk 1

# /var en raid
# ===============================
raiddev /dev/md4
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda8
raid-disk 0

device /dev/hdc8
raid-disk 1

# /tmp en raid
# ===============================
raiddev /dev/md5
raid-level 1
nr-raid-disks 2
nr-spare-disks 0
chunk-size 4

device /dev/hda9
raid-disk 0

device /dev/hdc9
raid-disk 1 [/QUOTE]

The Raid system is Raid1.
It think it should have recovered automatically, but it didnt.
I tried to boot on a liveCD to recover it.
I wasnt able to mount hda7/hda8/hda9 nor hdc8/hdc9.

I tried to use fsck but i read on the web that i had to use it on **md**x partition and not **hd**xx. I am not able to do that.

I need help please.

thanks in advance.

---

