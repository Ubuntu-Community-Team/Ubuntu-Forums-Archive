---
title: "disktest found MS DATA partitions"
date: 2015-03-10
forum: General Help
---

### Post by attempt66 on 2015-03-10
my laptop installed win8 and ubuntu 10.4
but I delete the partitions table '
then I try to recovery it using disktest
disktest says there is intel partitions table in the disk
but my disk is GTP
So I run the search under GTP
then I got original partitions back
but they are in MS DATA form, not NTFS

---

### Post by oldfred on 2015-03-10
I think you are mixing partitioning type and formats.

Drives are partitioned with the old MBR(msdos) or the newer gpt(GUID) type. And gpt has a protective MBR, just so old partition tools like fdisk to not automatically reformat it. All gpt drives should have one MBR partition entry saying drive is gpt.

And then you have GUID type code of partitions.
About 2/3's way down are the partition types.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
Different tools show descriptions and use different shortcut codes. 
If you use gdisk the efi partition is ef00, but with parted or gparted it is the boot flag. But the real code the the very long GUID shown in table above.

And then you have formats like ext4 as most common with Linux and NTFS as most common with Windows.
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

So on a gpt partitioned drive, you have an efi partition formatted FAT32, or a Windows data partition formatted NTFS. 
Only in the last couple of years was a separate data partition type added for Linux data so some tools may still show a Windows data type for a Linux formatted partition.

 Change type code  to 8300 with dual booting with Windows on gpt
[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)

---

