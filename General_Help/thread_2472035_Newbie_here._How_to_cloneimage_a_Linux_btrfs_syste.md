---
title: "Newbie here. How to clone/image a Linux btrfs system?"
date: 2022-02-16
forum: General Help
---

### Post by Advait on 2022-02-16
[COLOR=#000000][FONT=Arial]I’m currently using Ubuntu 21.10 with ext4 file system. I’m thinking of switching to 21.10 btrfs. I did some googling and looks like Clonezilla doesn’t work with btrfs. I use Clonezilla daily to clone my ext4 system. Works great and easy to use.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Since Clonezilla doesn’t work with btrfs, what do Linux users use to successfully and easily clone a btrfs system?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Remember, I’m a newbie so a solution that involves lots of command line knowledge will definitely not work for me. I need a simple solution like Clonezilla.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I looked at a Partclone video [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial]_[https://www.youtube.com/watch?v=-5dO2VAlGeM](https://www.youtube.com/watch?v=-5dO2VAlGeM)_[/FONT][/COLOR]]("https://www.youtube.com/watch?v=-5dO2VAlGeM")[COLOR=#000000][FONT=Arial] and it’s way too complicated for a newbie like me.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-02-16
LOL. Well let me explain this then...

You are not wanting to "clone" a disk... Cloning a disk would be like it's name (Clone), where that would mean that the disk created would be an exact mirror image of the original.

But you said, that is not what you want, right? What you want is to create another disk, 'like' the original, but with any partition except maybe the EFI partition (it UEFI) using BTRFS... Right?

My suggestion would be an Ubuntu LiveCD, using GParted and look at both disks to create partitions of the same type on the target Drive, which the EFI partition will be marked as ESP and Boot, formatted as Fat32. The rest of the Partitions will be the same as the source disk, except formatted as btrfs, instead of ext4. Then the swap partition as swap filesystem.

When down, you would open a graphical terminal session, using dd to copy the source EFI partition contents, to the target... Then use rsync commands to copy the the contents of the source partitions to the target partitions. So two to 4 commands in terminal.

Unfortunately, we cannot come up with those commands until we see how the disk is laid out for the original disk...  Which would be three commands
```

sudo fdisk -l
sudo blkid
lsblk

```
Please post the results of those commands within CODE TAGS like this:
[noparse]```

Output pasted here

```[/noparse]

---

### Post by Advait on 2022-02-16
> **MAFoElffen said:**
> LOL. Well let me explain this then...

You are not wanting to "clone" a disk... Cloning a disk would be like it's name (Clone), where that would mean that the disk created would be an exact mirror image of the original.

Unless I'm misunderstanding something, I want a clone of my system disk. If I understand correctly, I can restore a clone to my system drive and it will boot up normally.

Also, I'm not dual booting. Only Ubuntu 21.10 ext4 exists on my system drive. And I'm aware there may be some small partitions also, but I have no knowledge of what they are. Clonezilla clones everything and I don't have to think about those things.

> But you said, that is not what you want, right? What you want is to create another disk, 'like' the original, but with any partition except maybe the EFI partition (it UEFI) using BTRFS... Right?

As I mentioned, based on my understanding, I want to make a clone of my system drive to an external drive.

> My suggestion would be an Ubuntu LiveCD, using GParted and look at both disks to create partitions of the same type on the target Drive, which the EFI partition will be marked as ESP and Boot, formatted as Fat32. The rest of the Partitions will be the same as the source disk, except formatted as btrfs, instead of ext4. Then the swap partition as swap filesystem.

Thanks for the info, but this is *way* above my head. I need something simple like Clonezilla. Do you know of an app that can easily clone a btrfs system drive the way Clonezilla can easily clone an ext4 system drive to an external drive?

> When down, you would open a graphical terminal session, using dd to copy the source EFI partition contents, to the target... Then use rsync commands to copy the the contents of the source partitions to the target partitions. So two to 4 commands in terminal.

Again, I offer my thanks for this info, but it is *way* above my head.

> Unfortunately, we cannot come up with those commands until we see how the disk is laid out for the original disk...  Which would be three commands
```

sudo fdisk -l
sudo blkid
lsblk

```
Please post the results of those commands within CODE TAGS like this:
[noparse]```

Output pasted here

```[/noparse]

Sure, the output is here: [https://docs.google.com/document/d/1uFyn-B46s6iVitIcJBn13qb6vNmL8R24JILVdLb_qfo/edit?usp=sharing](https://docs.google.com/document/d/1uFyn-B46s6iVitIcJBn13qb6vNmL8R24JILVdLb_qfo/edit?usp=sharing) There's a lot of output so I copied to a separate doc.

Update, I tried to post the output here but got a "security token" error.

---

### Post by mastablasta on 2022-02-16
> **Advait said:**
> 
Also, I'm not dual booting. Only Ubuntu 21.10 ext4 exists on my system drive. And I'm aware there may be some small partitions also, but I have no knowledge of what they are. Clonezilla clones everything and I don't have to think about those things.

As I mentioned, based on my understanding, I want to make a clone of my system drive to an external drive.


clone means bit by bit is copied to another drive. so whatever you have now is copied exactly as it is (bit by bit) to another disk.
disk image is when image (again bit by bit ) is created and then you can restore it, copy it etc. to another drive-

> 
Thanks for the info, but this is *way* above my head. I need something simple like Clonezilla. Do you know of an app that can easily clone a btrfs system drive the way Clonezilla can easily clone an ext4 system drive to an external drive?


From Cloenzilla features:
> 
[LIST]
[*]Many File systems are supported: (1) ext2, ext3, ext4, reiserfs, reiser4, xfs, jfs, **[COLOR=#ff0000]btrfs[/COLOR]**, f2fs and nilfs2 of GNU/Linux, (2) FAT12, FAT16, FAT32, NTFS of MS Windows, (3) HFS+ of Mac OS, (4) UFS of FreeBSD, NetBSD, and OpenBSD, (5) minix of Minix, and (6) VMFS3 and VMFS5 of VMWare ESX. Therefore you can clone GNU/Linux, MS windows, Intel-based Mac OS, FreeBSD, NetBSD, OpenBSD, Minix, VMWare ESX and Chrome OS/Chromium OS, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored by [Partclone]("http://partclone.org/"). For unsupported file system, sector-to-sector copy is done by [dd]("https://en.wikipedia.org/wiki/Dd_(Unix)") in Clonezilla.
[/LIST]



alternately you can use various backup applications like Duplicati, Duplicity, Back-in-time, Areca, rsync...to backup only data and configuration files and maybe list of aplications. System files dont' really need to be backed up as much since they are installed fast with fresh installation.

EDIT: if Clonezilla really does not work, here are some suggestions from Manjaro users: [https://forum.manjaro.org/t/cannot-clone-btrfs-boot-drive-with-clonezilla/78836](https://forum.manjaro.org/t/cannot-clone-btrfs-boot-drive-with-clonezilla/78836)

---

### Post by SeijiSensei on 2022-02-16
I used the ddrescue utility to clone an SSD drive onto another device of identical size.  You first need to install it with
```
sudo apt install gddrescue
```. Scan the manual page before you begin ("man ddrescue").  

In my case I used a SATA-to-USB converter like [this one](https://www.newegg.com/unitek-y-1099new-usb-to-sata/p/35G-00DP-00001?Item=9SIA2BP8Y85738&Description=sata%20to%20usb&cm_re=sata_to%20usb-_-9SIA2BP8Y85738-_-Product&cm_sp=SP-_-548090-_-0-_-6-_-9SIA2BP8Y85738-_-sata%20to%20usb-_-sata|to|usb-_-3) to connect the target drive. Then it's a simple
```
sudo ddrescue /dev/sda /dev/sdb
```
or similar depending on how your drives are recogized.

ddrescue uses the "dd" command to do a bit-by-bit copy of the source device onto the target. It ignores the filesystem on the source drive entirely.

---

### Post by Advait on 2022-02-16
So it does support btrfs. Great. I read on another site that it doesn't (maybe that was outdated). If Clonezilla does indeed support btrfs, then I'm all set! Thanks for the info. O:)

And I'll research the snapshot backup capabilities inherent in btrfs and try to make full use of them.

---

### Post by MAFoElffen on 2022-02-16
But you need to understand (from what you said in your fist post) that your current Linux installation is on a ext4 filesystem, not btrfs. You said you wanted to try btrfs... Which would mean that you would need to change the filesystem underneath where all your files exist currently. 
> **Advait said:**
> [COLOR=#000000][FONT=Arial]I&#8217;m currently using Ubuntu 21.10 with ext4 file system. [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]I&#8217;m thinking of switching to 21.10 btrfs.[/FONT][/COLOR]
To try to paint a visual picture in your head, if a ext4 filesystem was the carpet in a room ( a partition), and you wanted to replace the carpet to a btrfs filesystem... And all the files were the furniture in that room, you have to move the furniture so you can replace the carpet... Then you put the furniture back in...

So to create a disk where the partitions have a different filesystem, you recreate the partitions on the new disk, format those new partitions wit the new filesystem, then copy the files on top of that new filesystem in that partition.

None of those GUI tools are going to do that "for you". Using those tools... Copying "bit by bit," the result of your new "clone/image" will still be on the "ext4" filesystem type... If you paid someone  to replace your carpet to something else, and after it was done, arrived home and found that same carpet there in that room, I imagine you would not be happy with that person, right?

@mastablasta & @SeijiSensei -- Did you both miss that important piece in the first two sentences of Post #1?

@Advait -- Good luck with that. I contacted and asked some other members to try to explain this to you...

---

### Post by Advait on 2022-02-16
> **MAFoElffen said:**
> But you need to understand (from what you said in your fist post) that your current Linux installation is on a ext4 filesystem, not btrfs. You said you wanted to try btrfs... Which would mean that you would need to change the filesystem underneath where all your files exist currently. 

None of those tools are going to do that "for you". Using those tools... Copying "bit by bit," the result of your new "clone/image" will still be the "ext4" filesystem...

@mastablasta & @SeijiSensei -- Did you both miss that important piece in the first two sentences of Post #1?

@Advait -- Good luck with that. I contacted and asked some other members to try to explain this to you...

Good point. To clarify, I plan to switch to btrfs by making lots of data backups, then wipe out my 21.10 ext4 and clean install 21.10 btrfs.

There's a btrfs conversion app I'm tempted to try, but doing a clean install feels better.

---

### Post by Impavidus on 2022-02-16
Most Ubuntu users don't use btrfs and most don't use cloning as part of their backup routine. (I understand that cloning is part of your backup routine, not of your strategy to get on an btrfs filesystem.)

To clone a filesystem, the cloning application doesn't have to know anything about the filesystem. It can simply make a bit by bit copy. But some cloning tools are smarter than that. If the cloning tool understands the filesystem being copied, it can skip the parts that are unused, thereby reducing filesize. Those parts can be added again when restoring the clone. Basically, you can put a compressed clone on your backup drive and get it back to the original size and contents when restoring the backup, except that the unused parts, which may contain fragments of old files (especially in spinning hard drives; on SSDs these get wiped periodically), get blanked. And some cloning tools may be able to do this trick on ext4, but not on btrfs.

So, if you want btrfs and still want to clone, you'll have to use uncompressed clones. But I wouldn't clone.

---

### Post by MAFoElffen on 2022-02-16
Now that brings up something simpler, from a completely different perspective... If you use a "backup application" to backup your files to another drive or partition, it copies the "files"... It doesn't care about the filesystem. 

And the fstab file uses the UUIDs of the partitions to make it's mounts. Grub-EFI uses the UUIDs of the partitions to boot. (not the UUID of the filesystem.)

Then you could format the partition to whatever filesystem you want (as long as it is a Linux Filesystem). Then you could restore your files back into that partition. That is possible to do completely with GUI toolsets.

If you did decide to re-install a new, fresh install, you just pick "Something Else" and when you pick the filesystem, you would just select "btrfs" as the filesystem, instead of the default ext4... (over simplified, but yes.)

---

### Post by TheFu on 2022-02-16
How to say this nicely.   A bit-for-bit copy is a extremely inefficient and completely unnecessary 99.9% of the time. There are so many better options. Oh, so many.

Especially if you have an advanced file system like BTRFS.  Please look into the snapshot capabilities of that file system/volume manager and use those to quiese the data, then use whatever backup tool (file based is best, fastest, most efficient) to get the snapshot data copied to some other storage.  Snapshots aren't backups, but they are extremely useful in creating a clean backup set.

Also, please don't ever span BTRFS volumes across multiple drives (storage devices) of any sort. There are nasty failure modes when more than 1 disk use used. Beware.  Total data loss is very possible.  There's an Ars Technica article about it that everyone using BTRFS needs to read AND understand.

For a laptop with 1 storage device, BTRFS is a great idea these days.

---

### Post by Advait on 2022-02-16
> **MAFoElffen said:**
> Now that brings up something simpler, from a completely different perspective... If you use a "backup application" to backup your files to another drive or partition, it copies the "files"... It doesn't care about the filesystem. 

And the fstab file uses the UUIDs of the partitions to make it's mounts. Grub-EFI uses the UUIDs of the partitions to boot. (not the UUID of the filesystem.)

Then you could format the partition to whatever filesystem you want (as long as it is a Linux Filesystem). Then you could restore your files back into that partition. That is possible to do completely with GUI toolsets.

If you did decide to re-install a new, fresh install, you just pick "Something Else" and when you pick the filesystem, you would just select "btrfs" as the filesystem, instead of the default ext4... (over simplified, but yes.)

Yes, I use Restic and FreeFileSync for user file backup. And I use Clonezilla to have a bootable and restorable *complete* backup of my system drive. Of course, both types of backups are needed for optimal data integrity.

The stuff about fstab, UUIDs and the rest was all over my head. I've never dealt with that stuff and to learn it would take more time than I have. Restic, FFS and Clonezilla take care of all my backup needs without needing to spend time learning lots of detail about filesystems, partitions, etc. I would love to have the time to learn that stuff, but I've got lots of higher priorities.

Yes, when I first installed Ubuntu I remember seeing the "something else" option for filesystem. That's what I plan to do.

---

### Post by Advait on 2022-02-16
> **TheFu said:**
> How to say this nicely.   A bit-for-bit copy is a extremely inefficient and completely unnecessary 99.9% of the time. There are so many better options. Oh, so many.

Especially if you have an advanced file system like BTRFS.  Please look into the snapshot capabilities of that file system/volume manager and use those to quiese the data, then use whatever backup tool (file based is best, fastest, most efficient) to get the snapshot data copied to some other storage.  Snapshots aren't backups, but they are extremely useful in creating a clean backup set.

Also, please don't every span BTRFS volumes across multiple drives (storage devices) of any sort. There are nasty failure modes when more than 1 disk use issued. Beware.  Total data loss is very possible.  There's an Ars Technica article about it that everyone using BTRFS needs to read AND understand.

For a laptop with 1 storage device, BTRFS is a great idea these days.

If my main system drive dies, having a perfect bootable and restorable clone makes it easy to recreate my system. And Clonezilla only takes about 25 min to clone my 2TB system drive. So I can easily make a clone during a meal.

And I use Restic and FreeFileSync for multiple backups of just my user data files.

And yes, I will research and use all the snapshot and backup capabilities of btrfs.

---

