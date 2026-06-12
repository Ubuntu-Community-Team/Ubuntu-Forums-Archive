---
title: "UUID Boot Problem in Fiesty"
date: 2007-06-16
forum: General Help
---

### Post by briantipton on 2007-06-16
I have been trying to track down a problem with my Fiesty boot sequence.  When the computer boots and the OS checks the file system, it computes the UUID incorrectly for the /boot partition.  Since it cannot find the partition in the /etc/fstab, it stops and goes to an emergency (?) shell.  All uuid commands from this point forward produce a different  UUID which **is** in the /etc/fstab.

/var/log/fsck/checkfs contains:
```
Log of fsck -C -R -A -a 
Fri Jun 15 23:32:55 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda1: clean, 32/32128 files, 26597/128488 blocks
fsck.ext3: Unable to resolve 'UUID=a8d2392b-2531-4afc-a1d9-5504764dbd76'

fsck died with exit status 8

Fri Jun 15 23:32:56 2007
----------------
```

ls /dev/disk/by-uuid/ -alh produces:
```
lrwxrwxrwx 1 root root  10 2007-06-15 18:42 d8e23230-30c4-4ebb-be64-3b03ed801a8b -> ../../sda1
```

and /etc/fstab contains:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e1e5486f-0556-403f-bf94-b46dd531dd3b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=d8e23230-30c4-4ebb-be64-3b03ed801a8b /boot           ext3    defaults        0       2
# /dev/sdb6
UUID=a8d2392b-2531-4afc-a1d9-5504764dbd76 /home           ext3    defaults        0       2
# /dev/sdb7
UUID=41435d0e-82f8-418d-8c0c-0ec23bad8012 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda2 /media/winroot ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

Note that the post-boot-problem commands all have the same UUID for /dev/sda1 while the checkfs during boot computes it differently.

Any ideas as to how to fix this so that the computer will boot without stopping?

Thanks.

Brian

*** UPDATE 6/16/2007 *** The problem is not /dev/sda1 but /dev/sdb6.  The UUIDs are the same at boot and in /etc/fstab!

---

### Post by confused57 on 2007-06-16
The UUID your Feisty boot is having trouble finding is your /home partition.

What you can do is boot the live cd, open a terminal, & see what your UUID is for /home:
```
blkid
```

---

### Post by briantipton on 2007-06-16
Should have carefully read the UUIDs, huh? :oops:

I will try your suggestion and see what happens.  Didn't install with a live CD though, so I will have to burn one.

Thanks.

Brian

---

### Post by drs305 on 2007-06-16
If that doesn't work, why not just change the UUIDs to the /dev/sdXX settings? That will fix it and then you can see what all your correct UUIDs are with a running system.

Backup your fstab first.

---

### Post by KrazyPenguin on 2007-06-16
This works:

[SIZE="4"]UUID Error at boot up (after making changes to partitions)

Open Terminal -> blkid
This will give the correct UUIDs.

Goto /etc/fstab and in admin mode find the UUID that is different
(Hint: the partition changed will be it)
and copy from terminal and paste with the correct UUID.
Reboot and should work.
[/SIZE]

No need to be root to run blkid.   
No need for a live cd.  :shock:

Good luck!!!
;-)

---

### Post by briantipton on 2007-06-17
Thanks to everyone's suggestions!

Alright, I tied blkid and got the answer I expected.  The same UUID was generated that was already in the /etc/fstab file.  The device (my mistake earlier) I am interested in is /dev/sdb6 not /dev/sda1.  I misread the error message at boot.

The sdb device is a USB drive external to the laptop this is running on, if that helps.

Still looking for answers.

Brian Tipton

---

