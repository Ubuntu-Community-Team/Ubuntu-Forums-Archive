---
title: "HDD recovery for Ubuntu Live CD"
date: 2005-05-07
forum: General Help
---

### Post by elmimmo on 2005-05-07
Hi,

I do not know if this is the proper place to ask for free support, but no other forum seemed more appropriate, so please forgive me if this is not the place.

I have a PC notebook with a seemingly dead hard disk, not backed up, that I would like to try to recover before trying the final format-and-say-bye-bye-to-everything. I still do not know if the error is of data corruption or mechanical malfunction.

I wondered if anyone can think of some sort of an application that does more or less the same things as "Scandisk" or "Norton Disk Doctor" for Windows, that I can use from an Ubuntu Live CD (which I am using right now to plead for help [-o< ).

The added problem is that my only other computer is an iMac G3, so removing the HDD and plugging it onto the other computer is not a possibility.

I tried simply booting with the Live CD, mounting the HDD in order to later on save what could be saved without any recovery method by transfering it through the network to the iMac. But I am quite an ignorant in Linux, and mounting it did not work, so it is not like I can do much more by myself.

In order to mount the disk, which I have no clue wether is FAT32 or NTSC formatted I opened "Root Terminal" from the menu Applications > System . And wrote:```
mkdir /bad-disk
mount /dev/hda1 /bad-disk
```Trying to access that directory afterwards, froze Ubuntu. Rebooting and trying the following ```
mkdir /bad-disk
mount -t ntsf /dev/hda1 /bad-disk
```Reported the following error```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```and typing "dmesg | tail" reported the following```
mtrr: base(0xb0020000) is not aligned on a size(0x300000) boundary
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
```

I guess the first way to mount it was good enough and that the real problem is that the data is corrupted (to a higher or lower level). But that is just a guess without a knowledgeable base, and anyhow does not help me much in order to be able to try other things.

So, does anyone have any thoughts on what else I could try?

   elmimmo

PS: By the way, I tried to mount /dev/hda1 because that in Device Manager there is a "Volume" listed branching from the "blah blah Ultra ATA controller" with "block.device" parameter set as "Type: string; Value: /dev/hda1". The only other device connected to that controller is a "Slimline DVDRW blah", so I guess that the former Volume refers to the HDD. But, as I said, I am quite an ignorant regarding Linux.

---

### Post by kvidell on 2005-05-07
I replied here: [http://ubuntuforums.org/showthread.php?t=32328](http://ubuntuforums.org/showthread.php?t=32328)

---

### Post by elmimmo on 2005-05-07
Thanks so much for the answer. This is the result of the first cautious step with fsck as you suggested:```
root@ubuntu:/home/ubuntu # fsck /dev/hda1
fsck 1.35 (28-Feb-2004)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup .
Differences: (offset:original/backup)
  65:03/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Read 32 bytes at 683470848:Input/output error
```Backup? Does a FAT32 system back up itself? Should I try (at my own responsability of course) action 2, or is it deemed to give the final hit to whatever might have been recoverable?

---

### Post by kvidell on 2005-05-07
[QUOTE=elmimmo]Backup? Does a FAT32 system back up itself? Should I try (at my own responsability of course) action 2, or is it deemed to give the final hit to whatever might have been recoverable?[/QUOTE]I'm not sure how it would have backed itself up, or to where.
I'm particularly unfamiliar with FAT though. My thinking is how would it restore a backup that quite possibly doesn't exist... and if it was dull enough to store the backup on the same volume, what's to say the backup isn't corrupt as well by now?

Seems strange. Those are the only options you can juice out of it for repair, though?
- Kev

---

