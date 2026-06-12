---
title: "Disk Format for Backups - Flash or Hard Drive - EXT4 - FAT32"
date: 2014-07-28
forum: General Help
---

### Post by KAWill70 on 2014-07-28
The link below mentions an incompatibility between EXT4 and NTFS for backing up Linux files.  The main reason seems to be special characters supported by EXT4 but not NTFS.  Another reason is that EXT4 supports an empty character at the end of file names.

[http://some-other-linux-tweak.blogspot.com/2012/01/copy-files-successfully-from-ext3ext4.html](http://some-other-linux-tweak.blogspot.com/2012/01/copy-files-successfully-from-ext3ext4.html)

What disk format are others using for file backup in Linux?

I assume that EXT4 is a good choice.  What about Flash drives that are typically formatted FAT32?  Are there any problems with the special characters used in EXT4?

---

### Post by Bucky Ball on 2014-07-28
*Thread moved to **General Help**.*

EXT4 fine for a USB dongle. If you're not going to use the drive/partition with Win, EXT it is. Definitely don't use FAT. It has size limitations.

Never had an issue with EXT to NTFS, myself, but I never use spaces or unusual characters in my file names. ;)

Good luck.

---

### Post by ajgreeny on 2014-07-28
It will also depend to an extent on what application you use for your backups and if you archive them or not..

You can use ntfs if you tar or zip your backups before transferring them as the archive will keep all permissions whatever filesystem you format to, but don't use fat32 as that will limit you to a 4GB tar, nowhere near large enough for most modern systems.

However, I have to agree that ext2, 3 or 4 would be best so long as you do not need the backup to be used by windows as well as linux.  I use ext3 on my external disk.

---

### Post by KAWill70 on 2014-07-28
Thanks Bucky Ball and ajgreeny for the help.  EXT does sound like the best choice.

My concern was not only full backups but occasionally just copying a few files to a Flash drive or other media.  Flash drives are often formatted FAT32.  The link below suggests that FAT32 does not allow all the characters that might be used with EXT4.

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

I agree on having control over my file names, but one could also be dealing with files created by someone else.

The link in my original post showed a "white space" at the end of a file name about half way down the page in the example.  I can see why NTFS would have a problem with that file, but it's not clear how that file name is actually created.  Maybe it's the result of just using the space bar.

---

### Post by Bucky Ball on 2014-07-29
Ya, just a space. Don't use them. Forget FAT. As mentioned, it has size limitations.

---

### Post by M._Gruber on 2014-07-29
There are tools for Windows which allow you to mount EXT volumes. Even EXT4 volumes can be mounted, although only as EXT3.

---

### Post by M._Gruber on 2014-07-29
Aside from that I'm using an NTFS volume mounted with ntfs-3g to backup portions of my Linux system since years without any problems, so that's also a way you can go.

---

