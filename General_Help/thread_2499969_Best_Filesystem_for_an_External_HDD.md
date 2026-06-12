---
title: "Best Filesystem for an External HDD"
date: 2024-08-16
forum: General Help
---

### Post by nicolasdentremont on 2024-08-16
Hey all. I'm getting a Toshiba 2TB external HDD to store backup copies of files, movies and stuff I don't need to access very often. It's only going to be accessed by my computer running Ubuntu. I figure it's going to come with a Microsoft oriented filesystem on it. What filesystem would you recommend for use with Linux? I read that EXT4 and BTRFS are good choices.

---

### Post by guiverc on 2024-08-17
Almost all my external & backup drives are *ext4* as I've always believed simple is best, and never had troubles with this POSIX compatible format.

I'd expect I have some older NTFS external drives (*where not all POSIX file-system data is stored, so no critical or backup data goes to those*), but any data on those [NTFS] will be over a decade old. If you expect to use the devices on older media players or windows devices then NTFS makes some sense (*but consider storing file-system metadata in another way*)

---

### Post by Autodave on 2024-08-17
If only going to be used on linux system, ext4.

---

### Post by oldfred on 2024-08-17
Even if planned as a data only drive, I like to do a smaller install.
Becomes another emergency boot option. I only add some repair tools like gparted, but often add repair ISOs to directly boot from grub.
But without snaps (I always remove snaps) & not a lot of added programs or data in /home, / (root) does not have to be large or 30 to 40GB.
And a lighter weight flavor often works better from external devices.
Make sure to use gpt partitioning and make ESP as first partition, so you can make it bootable later, even if you do not want to now.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I use Kubuntu which is more mid weight but has worked on older & external drives for me.

---

### Post by TheFu on 2024-08-17
ext4.  Simple. Journaled. Easy to manage.  

Be certain to setup partitions as needed. With larger HDDs, it is worth considering what size you might want for the largest partition.  This is about limiting how much data can be written. It is best to have an exact, specific, size, so when you need to swap in a new HDD/SSD in a few years, you can retain the exact same size even if the new HDD is 2x-5x larger.   For example, I standardized on 4TB partitions many years ago because 4TB was the right price for my needs.  Since then, regardless of the actual disk size, I've always gotten them either at 4TB or multiples of 4TB to make drop-in replacement easy.   And all of them have ext4 as their file system.

---

### Post by nicolasdentremont on 2024-08-17
Thanks everyone for all the info. I'll probably go with EXT4. I figure I'll stick to one partition for now.

---

### Post by werewulf75 on 2024-08-20
Yes, all USB  disks and sticks come formatted with FAT32.

If you don't need to use it for data exchange to/from Windows, then ext4 is definitely the one to go for. But you may want to use at least two partitions (GPT partition table). The first could be a small, say 200 GB, one, for relatively unimportant stuff. Encrypt this, and use the rest for a 'hidden' encrypted partition. Encryption is always a good plan for added security.

If however you need to interact with Windows, then NTFS would make life easier. Although Windows now seems to be able to read ext4, it doesn't write to it. At least, it doesn't seem to do it here on my little Windows 10 system with WSL. (Not really a problem as I prefer copying to/from Windows from within Ubuntu.)

---

### Post by TheFu on 2024-08-21
For HDDs and SSDs, the choices are typcially ext4 and NTFS. NTFS only if the drive will be routinely connected directly (not over the network) to MS-Windows.

For flash storage like SDHC/microSD and those little USB-flash drives, then the better choices are file systems that do not do journaling. That's because journals almost double the number of writes to the flash "cells", wearing them out 2x faster.  That's a simplistic view, but close enough.

So, for flash storage and needs to be cross platform, choose exFAT (not FAT32).  

For flash storage that will be used only by your Linux systems, install and use f2fs.  This is a "Flash Friendly File System".  If other Linux systems need access, then you are left with ext2.  That's a file system from when Linux didn't have journaled file systems.  It should be on every Linux, since often the /boot/ partition was using ext2 until recently.  Beware, ext2 is being Deprecated.  Lots of embedded Linux systems use ext2 today.  [https://www.phoronix.com/news/Linux-6.9-Deprecates-EXT2](https://www.phoronix.com/news/Linux-6.9-Deprecates-EXT2) so in 10 yrs, it won't be available. We have time.  

I'm confused that ext3 isn't also being deprecated, since it is just ext2 with addon (tacked on) journaling. In the old days, when ext3 failed for some reason, we could mount that storage using ext2 instead. Just sayin'.  

There are lots of reasons for these suggestions. Wikipedia has information on how each file system works, but I suspect you don't want to read that, so asked for a summary here.

As for the partition table type, that's easy.  Always setup GPT and not MBR.  This is the Linux answer.  MSFT placed some arbitrary limitations on when GPT and MBR could be used. No logic behind that, but whatever. MSFT does lots of crazy things for unknown reasons ... or reasons they don't want the world to know.

Lastly.  If you have specific hardware devices that will access the storage devices that only supports file system X and Y, then you really don't have any choice.  You need to choose the best option between X and Y then use that.  

A few examples, I have a camera that only supports FAT32. No other file system. If I want to use it with that camera (SDHC media), then it must be formatted FAT32.
Another example, is an HDMI video recorder device.  It supports NTFS and FAT32, nothing else. It has a USB storage interface, so I can connect lots of different storage to it. Currently, I'm using a SATA SSD inside a USBc enclosure.  It is formatted as NTFS.  There are lots and lots of reasons to avoid FAT32, so my rule about that is only use FAT32 when there **isn't any other choice.**  

BTW, did everyone see that MSFT has decided to remove their arbitrary size limit on FAT32 partitions?  To be fair, FAT32 is designed for smaller storage and the arbitrary 32GB limit that MSFT silently added in WinXP without telling anyone wasn't unreasonable as storage devices  became larger and larger.  [https://arstechnica.com/gadgets/2024/08/new-windows-11-build-removes-ancient-arbitrary-32gb-size-limit-for-fat32-disks/](https://arstechnica.com/gadgets/2024/08/new-windows-11-build-removes-ancient-arbitrary-32gb-size-limit-for-fat32-disks/) is from August 16, 2024!  They will allow FAT32 to be 2TB - the amount of wasted storage that will enable is just crazy - and it is only for recent Win11 builds.  Guess MSFT isn't getting enough people to drop prior Windows releases?  IDK.

And we can't just use NTFS everywhere. Linux requires native Linux file systems with capabilities that NTFS doesn't have.  For pure data that doesn't need security on Linux, NTFS is fine.  For the OS, HOME directories and other system directories of Linux, it won't work currently.  I've read that the systemd team has been working on making HOME directories allow NTFS, but that has been in-the-works for over 5 yrs now. I don't see it, but I'm stupid that way.

A table with file system limitations: [https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems)
Usually, there is a limit to the size a single file can be, the length of the filename, the length of directory names, the different characters allowed in any named portions and the total file system size allowed.  The current file systems commonly used, while they do have limitations, those limitations tend to be unimportant for nearly everyone.  We just don't come close to hitting them anymore.

I'd also like to be clear. NTFS is an excellent, journaled, file system. If it isn't abused, it is extremely solid with data loss unlikely for logical corruption issues on MSFT OSes.  The NTFS used by Linux is a reverse-engineered variant. It has flaws, but works "well enough" for most people.
Linux has a number of extremely solid file systems available. ext4, xfs, zfs, f2fs are all very stable and don't really have any logical corruption problems.  BTRFS for specific uses is stable, but there are still some seldom-used features that risk corruption. That's too bad.  XFS had a performance lead and longer life than the other options I listed.  It has never allowed reducing the size of the file system, however. This can be very important or not important at all. Just depends on the administrator.  Last week, I needed to reduce a file system from 450GB to 35GB. If it was xfs, that wouldn't have been possible. Thankfully, it was ext4.

Anyway, I dumped a lot of stuff here. Hopefully, someone finds it useful, someday, and before a new file system is created that replaces them all. ;)

---

### Post by nicolasdentremont on 2024-08-21
Lots of good info there. EXT4 is going to work fine for what I need. It came it yesterday and I moved my stuff from the wife's external HDD. I used to use her drive but it messed up one day while copying files and I had to use her PC to repair it with Windows. That's why I wanted my own with a Linux oriented filesystem.

---

### Post by TheFu on 2024-08-21
"backups" are only a backup if the data is stored 3 places.
[LIST=1]
[*]Primary storage
[*]Backup storage (local)
[*]Remote backup storage (in a different part of the world) 500+km away; not impacted by local disasters (hurricanes, earthquakes, etc)
[/LIST]

People often make the mistake of considering a "backup drive" as the backup, then delete the files from the main storage. That isn't a backup. It is a second disk with primary storage on it.

---

### Post by nicolasdentremont on 2024-08-22
> **TheFu said:**
> "backups" are only a backup if the data is stored 3 places.
[LIST=1]
[*]Primary storage 
[*]Backup storage (local) 
[*]Remote backup storage (in a different part of the world) 500+km away; not impacted by local disasters (hurricanes, earthquakes, etc) 
[/LIST]

People often make the mistake of considering a "backup drive" as the backup, then delete the files from the main storage. That isn't a backup. It is a second disk with primary storage on it.

Looks like my work stuff is backed up at least. Although the remote storage is a Google Drive. I was thinking of switching to a different remote storage provider and setting up my own little server at home for the day-to-day remote access.

---

### Post by TheFu on 2024-08-22
> **nicolasdentremont said:**
> Looks like my work stuff is backed up at least. Although the remote storage is a Google Drive. I was thinking of switching to a different remote storage provider and setting up my own little server at home for the day-to-day remote access.

The actual data is only 50% of a backup. The file metadata, which is typically stored in the file system (owner, group, permissions, ACLs, xattrs) is the other 50%.  

Without both (or a 100% correct guess for the metadata), restoring will be useless.  Normally, only files stored in your HOME would **not need** the metadata, since you should know who the proper owner, group and permissions are for those HOME files.  A few of those files are really picky and won't work if the permissions are even a little off.  That's something everyone needs to learn on their own, I suppose.  A real backup tool should address all of these things and keep them versioned along with different versions of the files.

If you are just copying the files, those aren't proper backups.  Find a backup tool that supports versioning of the data AND the metadata.  There are lots of choices.  Watch out for hardlink-based backup tools.  They've been around forever and are efficient, fast, and better than so many other options, but they don't version the metadata.  When I was first burned by this issue, it sucked.

---

### Post by nicolasdentremont on 2024-08-22
> **TheFu said:**
> The actual data is only 50% of a backup. The file metadata, which is typically stored in the file system (owner, group, permissions, ACLs, xattrs) is the other 50%.  

Without both (or a 100% correct guess for the metadata), restoring will be useless.  Normally, only files stored in your HOME would **not need** the metadata, since you should know who the proper owner, group and permissions are for those HOME files.  A few of those files are really picky and won't work if the permissions are even a little off.  That's something everyone needs to learn on their own, I suppose.  A real backup tool should address all of these things and keep them versioned along with different versions of the files.

If you are just copying the files, those aren't proper backups.  Find a backup tool that supports versioning of the data AND the metadata.  There are lots of choices.  Watch out for hardlink-based backup tools.  They've been around forever and are efficient, fast, and better than so many other options, but they don't version the metadata.  When I was first burned by this issue, it sucked.

Finding a proper backup tool is definitely on my to-do list.

---

