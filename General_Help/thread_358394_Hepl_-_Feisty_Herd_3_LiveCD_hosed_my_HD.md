---
title: "Hepl - Feisty Herd 3 LiveCD hosed my HD"
date: 2007-02-10
forum: General Help
---

### Post by master_b on 2007-02-10
A couple of days ago I tried to install Kubuntu Feisty herd 3 (Live CD)on my laptop ( triple boot XP Home/XP Pro/Kubuntu 6.10) and the partition creation part of the Install hosed my hard drive.:confused: 

I've installed Ubuntu/Kubuntu many times ( I have it currently on 5 PCs) and had no problem with thie installation in any way before - I did nothing different here - reformat existing Kubuntu partition and keep existing Swap partition.

Now I have 2 XP partitions with bad partition table info, one partition ext3 empty except for "Lost and Found" - this was my Data partition and all data is gone - and what was my Kubuntu partition - now unformated - Swap has disappeared and space added to unformated partition.

Stupidly I did all of this before checking these Forums which warn of qparted problems ( providing that you search for the problem) with Feisty.

The Live CD of Feisty Herd 3 runs fine.

Here's the testdisk analysis of my hard drive


TestDisk 6.3, Data Recovery Utility, March 2006
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/hda - 60 GB / 55 GiB - CHS 116280 16 63
    PTestDisk 6.3, Data Recovery Utility, March 2006
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/hda - 60 GB / 55 GiB - CHS 116280 16 63
    Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 20479  15 63   20643777
D HPFS - NTFS          20479  12  1 40799  15 63   20482812
P Linux                40800   1  1 61598  15 63   20965329
D Linux                61598   8  1 63686  15 63    2105208 [/]
D Linux                63686   5  1 116264  15 63   52999317 [/]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
Enter: to continue

EXT3 Large file Sparse superblock Backup superblock, 10734 MB / 10236 MiBartition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 20479  15 63   20643777
D HPFS - NTFS          20479  12  1 40799  15 63   20482812
P Linux                40800   1  1 61598  15 63   20965329
D Linux                61598   8  1 63686  15 63    2105208 [/]
D Linux                63686   5  1 116264  15 63   52999317 [/]

As yet I haven't figured out how to use Testdisk to hopefully correct my problem - any advice appreciated.


master_b

---

### Post by master_b on 2007-02-11
Anybody?

Help please.

master_b

---

