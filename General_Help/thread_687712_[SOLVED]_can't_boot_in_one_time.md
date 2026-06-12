---
title: "[SOLVED] can't boot in one time"
date: 2008-02-04
forum: General Help
---

### Post by matthiayer on 2008-02-04
hi,

i have a grub with in it ubuntu, then there are two other systems, windows xp and another time ubuntu but that is my previous install with gutsy which had numerous errors..

so i installed qgrubeditor and deleted the second gutsy which isn't on my disk anymore, and after this i had some problems, first: when i boot it just stops booting and then says an error log is saved, en when i type reboot at that time, ubuntu starts.

so i thought it had to do with qgrubeditor, so i tried to undo the changes with qgrubeditor but then my grub was gone.

so i had to use the live cd and was able to get the old menu.lst back.
but now i still have the problem that it wont start in one time!!

this is the log at boot:

> Log of fsck -C -R -A -a 
Mon Feb  4 22:07:31 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=518445c3-274c-4e5c-bbf2-09984a78b450'

fsck died with exit status 8

Mon Feb  4 22:07:32 2008
----------------

---

### Post by dabl on 2008-02-04
Looks like a UUID number got changed -- this would happen if you formatted a partition or changed the size of it, for example.  If you run ```
blkid
``` it will show the partitions and the UUIDs on your system -- you may need to edit both /boot/grub/menu.lst and /etc/fstab to make them read the partitions correctly.

Here's a lot of help with Grub:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by matthiayer on 2008-02-04
i had 20 Gb i couldn't use after reinstalling, but it had to be ntfs formatted, so i formatted it in windows..

so what you say makes sense to me.
but can you give me a solution for my problem?

---

### Post by plucky on 2008-02-04
matthiayer,

Can you open a terminal by **Applications > Accessories > Terminal** and type in these commands and copy and paste them back here ```
blkid
``` and ```
cat /etc/fstab
```.You will find that one of your **UUID's** in your **fstab** file doesn't match the current UUID's on your disk as shown by the **blkid** command.

To change the UUID you need to edit your fstab file using ```
gksudo gedit /etc/fstab
``` and copying the correct UUID into the fstab file.

Hope this helps...

---

### Post by matthiayer on 2008-02-05
i've done what you said, i changed a few things but I still have the same problems..


```

/dev/sda1: UUID="EAC08914C088E7E1" TYPE="ntfs"
/dev/sda2: UUID="FCC0530AC052CA92" TYPE="ntfs"
/dev/sda3: UUID="ec05279d-b63e-4b43-badb-5215a90a6c22" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="f4edb7ce-0f59-48cb-a25b-a9742b3b45b3"
matthiayer@matthiayer-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ec05279d-b63e-4b43-badb-5215a90a6c22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EAC08914C088E7E1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=518445c3-274c-4e5c-bbf2-09984a78b450 /media/sda2     ext3    defaults        0       2
# /dev/sda5
UUID=f4edb7ce-0f59-48cb-a25b-a9742b3b45b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
matthiayer@matthiayer-laptop:~$   
```

---

### Post by plucky on 2008-02-05
```
matthiayer@matthiayer-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ec05279d-b63e-4b43-badb-5215a90a6c22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EAC08914C088E7E1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
[color=red]UUID=518445c3-274c-4e5c-bbf2-09984a78b450 /media/sda2     ext3    defaults        0       2[/color]
# /dev/sda5
UUID=f4edb7ce-0f59-48cb-a25b-a9742b3b45b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
matthiayer@matthiayer-laptop:~$
```

The highlighted line is incorrect as it is pointing to the partition that you reformatted to NTFS which changed the UUID.

I think you need to change it to ```
UUID=FCC0530AC052CA92 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
``` to reflect the new partition.

I have not added a new NTFS partition before,so you do this at your own risk if I am incorrect.

To edit fstab file ```
gksudo gedit /etc/fstab
``` after you have copied it with ```
sudo cp /etc/fstab /etc/fstab.bck
```

Good luck

---

### Post by matthiayer on 2008-02-05
thank you all for helping it works!!

---

