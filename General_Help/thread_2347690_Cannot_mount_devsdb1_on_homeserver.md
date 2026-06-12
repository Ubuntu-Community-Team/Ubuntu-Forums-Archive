---
title: "Cannot mount /dev/sdb1 on /home/server"
date: 2016-12-27
forum: General Help
---

### Post by jmason2 on 2016-12-27
Hello all,

Running 16.10 here on a headless system. Noticed my vnc was having issues reconnecting and did a hard restart on the machine. System came online but there is an issue mounting a drive. Running Gparted shows the drive is recognized and the data is still there. Just does not seem to be mounting.

> Could not mount /dev/sdb1 on /home/server/media
# mount -v /dev/sdb1 "/home/server/media"mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.


# mount -v -t ext4 /dev/sdb1 "/home/server/media"
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

fdisk -l output is:

> Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xaad6c5b9


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 608907263 608905216 290.4G 83 Linux
/dev/sda2       608909310 625141759  16232450   7.8G  5 Extended
/dev/sda5       608909312 625141759  16232448   7.8G 82 Linux swap / Solaris




Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 561B361F-CCE7-46D0-837F-81A84BBD4581


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 5860532223 5860530176  2.7T Linux filesystem




Disk /dev/sdh: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1AB5F0B7-72CD-4B11-8AF4-26E57F9D6C88


Device     Start        End    Sectors  Size Type
/dev/sdh1   1024 5860532223 5860531200  2.7T Microsoft basic data




Disk /dev/mapper/cryptswap1: 7.8 GiB, 8310489088 bytes, 16231424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Any help would be appreciated. Thank you!

---

### Post by SeijiSensei on 2016-12-28
Linux cannot determine the type of filesystem on /dev/sdb1.  If you're sure it should be an ext4 filesystem, try running fsck against it:
```
sudo fsck /dev/sdb1
```
and telling it to fix any errors if finds.

If fsck also fails, you've got a serious problem.  It may be that the data are not retrievable by conventional means, though programs like [testdisk and photorec]("http://www.cgsecurity.org/wiki/TestDisk_Download") might be able to help.

---

### Post by jmason2 on 2016-12-28
This worked wonders. Thank you for your help.

It appears there was a issue/ discrepancy with calculation of space and it needed a quick repair.

Is there something that I may have done to cause this? Or, is this something I should be concerned about in the future? Ie a drive replacement etc.?

---

### Post by SeijiSensei on 2016-12-28
> Noticed my vnc was having issues reconnecting and **did a hard restart** on the machine. 

The most common reason a filesystem fails the check is because the system was powered off rather than shut down gracefully from the menu or via the "shutdown" or "reboot" commands at the terminal prompt.  Ubuntu can often fix minor problems by automatically running fsck during the boot process, but some problems are serious enough to require manual repair.  

You may also have lost data as a result of this problem.  When the filesystem is not cleanly unmounted, there are open "file handles" that are discarded.  If the system was in the process of writing to the device, these incomplete files will leave the filesystem in an "unclean" state.

---

