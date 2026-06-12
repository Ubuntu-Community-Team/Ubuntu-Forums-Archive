---
title: "Ntfs -&gt; Fat32"
date: 2007-07-06
forum: General Help
---

### Post by gormen on 2007-07-06
I said goodbye to windowsxp and decided to install ubuntu, but due to lack of diskspace and lots of things i wanted to save i decided to convert 2 of my disks (2 partitions on each) from NTSF to FAT32 using partitionmagic. But during the last conversion i got a few errormessages and wasnt able to do anything else then press (ok) and continue. The conversion failed and the result was a few files and a folder with wierdlooking namnes on that partition.
When i do fdisk -l /dev/hda it says FAT32 for that partition.
Is the data gone forever? or is there some way to restore it?
(OFCOURSE i didnt make any rescuedisks and OFCOURSE it had to screw up the one partition that i was storing the most important files :( )

---

### Post by aquavitae on 2007-07-06
The problem may have been caused by large files - i.e. bigger than 2G.  Nfts can handle them, but fat32 can't.  Anywa, no good trying to work out what caused it! I don't have an immediate answer for you, but I do know that there are tools for recovering damaged partitions (fsck is one of them)  If you have enough space on another disk, I'd say first image the entire partition using dd:
dd if=/dev/hda1 of=imagefile
obviously replacing /dev/hda1 for the name of the partition.  Then at least if you totally screw it up you can get back to where you were (by reversing the if and of parameters of dd).  Try running fsck:
fsck /dev/hda1
If that doesn't work, have a look on google for recovering damaged partitions in linux.  I remember once finding instructions on how to recover data from a damaged flash drive (which would have worked if the flash drive hadn't been totally fried...) so the same instructions may help you.  But be warned - its a lot of messy command line stuff.

---

### Post by H3g3m0n on 2007-07-06
Converting from NTFS to FAT32 is pointless, you can use NTFS with read/write fine under Ubuntu, just 'apt-get install ntfs-config' then run 'ntfs-config'.

The speed is even fairly close to native file systems.

Obviously a Linux filesystem would be preferable but converting from NTFS to FAT32 doesn't really serve much purpose.

If you are ditching Linux entirely and are short on space for backing up files it might be better to shrink the NTFS partition, increase the size of Linux, move files across then repeat until there all across but you will not beable to use windows to access the file anymore if they are on a Linux partition (actually there are some ext3 drivers for windows around but I don't know how good they are) so make sure you ready for the switch otherwise just use ntfs-config to allow read write access to your file from within Linux.

---

### Post by az on 2007-07-06
> **aquavitae said:**
> 
If that doesn't work, have a look on google for recovering damaged partitions in linux.  I remember once finding instructions on how to recover data from a damaged flash drive (which would have worked if the flash drive hadn't been totally fried...) so the same instructions may help you.  But be warned - its a lot of messy command line stuff.

Use foremost or Photorec.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

