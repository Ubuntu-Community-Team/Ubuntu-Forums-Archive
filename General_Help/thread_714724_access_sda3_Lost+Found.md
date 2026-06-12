---
title: "access sda3 Lost+Found"
date: 2008-03-04
forum: General Help
---

### Post by addisor on 2008-03-04
For some reason I have a lost+found folder on sda3 of 21GB that i can't access, I'd like to use this partition for other things, what can I do to remdy this problem?


rob@rob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b95cd41-e9b7-4e9a-b1ef-6a17471a9f77 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=5b519497-e62f-467b-9ef7-49c556e5142a /home           ext3    defaults        0       2
# /dev/hda1
UUID=565540eb-bdaf-4de8-b3c1-991117c5d964 /media/hda1     ext3    defaults        0       2
# /dev/sda3
UUID=16788ee1-2615-41eb-8f49-c7686f128c65 /media/sda3     ext3    defaults        0       2
# /dev/hda5
UUID=487bd919-6692-41eb-ae08-db1d647c5668 none            swap    sw              0       0
# /dev/sda5
UUID=de30a1ae-caf3-4eed-92e8-4ab5c63994a5 none            swap    sw              0       0
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0


rob@rob-desktop:~$ sudo fdisk -l
[sudo] password for rob:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe366e366

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+  83  Linux
/dev/sda2            2933        5864    23551290   83  Linux
/dev/sda3            5865        8796    23551290   83  Linux
/dev/sda4            8797        9433     5116702+   5  Extended
/dev/sda5            8797        9433     5116671   82  Linux swap / Solaris

---

### Post by PmDematagoda on 2008-03-04
The Lost+Found folder is where the journal files of the drive/partition are kept, because of this that particular folder cannot be written to or read as any change to that folder could cause problems.

Are you able to write to the drive in general without the Lost+Found folder in particular?

---

### Post by addisor on 2008-03-04
No it says i dont have permission to write to this folder, been like that since gutsy install on sda, with 6.10 on hda.

---

### Post by PmDematagoda on 2008-03-04
> **addisor said:**
> No it says i dont have permission to write to this folder, been like that since gutsy install on sda, with 6.10 on hda.

No no, not writing to the lost+found folder, to the hard drive itself.

---

### Post by addisor on 2008-03-04
Can't drag n drop in nautilis but can copy to media/sda3 using terminal, but only as sudo.

---

### Post by PmDematagoda on 2008-03-04
Unmount the drive using:-
```
sudo umount /media/sda3
```
Then remount it using:-
```
sudo mount -t ext3 /dev/sda3 /media/sda3 -o rw
```
Then see if you can write to the hard drive.

---

### Post by addisor on 2008-03-04
tried to delete something i managed to copy threre whilst sudo in terminal. can't delete in nautilis even after unmount/remount. 

"/media/sda3...ols.pdf.odt" cannot be deleted because you do not have permissions to modify its parent folder.

---

### Post by PmDematagoda on 2008-03-04
> **addisor said:**
> tried to delete something i managed to copy threre whilst sudo in terminal. can't delete in nautilis even after unmount/remount. 

"/media/sda3...ols.pdf.odt" cannot be deleted because you do not have permissions to modify its parent folder.

That is a rather strange problem, I am really sorry, but I do not think I can help you further. You aught to wait for someone else to come along and help you with this.

---

### Post by chrisccoulson on 2008-03-04
It just seems like a case of not having the correct permissions to write to the area of the disk that you want to write to (especially seeing as you said you can copy files on to the volume using sudo). You certainly can't write to lost+found without using sudo or being root anyway, which is perfectly normal.

You probably can't write to the root of the volume without sudo at all (not without specifying some extra options in your fstab). However, being ext3, you should be able to use sudo mkdir to create a folder on /media/sda3, then chown it to yourself and chmod it to set up permissions so that you can read/write to the new folder.

I'd be more concerned about having 21GB in lost+found. fsck only puts stuff in there as a result of errors when checking the volume.

---

### Post by articpenguin on 2008-03-04
> **PmDematagoda said:**
> The Lost+Found folder is where the journal files of the drive/partition are kept, because of this that particular folder cannot be written to or read as any change to that folder could cause problems.

Are you able to write to the drive in general without the Lost+Found folder in particular?

No the Lost+Found folder is where fsck puts corrupted files. The folder usually has thousands of files on a reiserfs partition.

---

### Post by addisor on 2008-03-05
managed mkdir rob/media/sda3/stuff, then chown it ok but struggling with chmod. Can you point me in the right direction? happy to have access for all and read/write.

Managed a numeric chmod 777, thanks for help

---

