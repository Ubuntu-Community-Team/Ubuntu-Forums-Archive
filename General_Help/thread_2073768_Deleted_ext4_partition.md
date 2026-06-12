---
title: "Deleted ext4 partition"
date: 2012-10-20
forum: General Help
---

### Post by megsona on 2012-10-20
Hi forums,

i did a stupid thing, downloaded the latest 12.10 release and in my haste went for the reinstall option rather than 'other'.

I have a 500gb drive which had a 15gb OS partition at the beginning, a 6gb swap partition at the end and the rest (about 479gb) was partitioned for /home. I didn't stop to think that reinstallation would re-partition my drive.

So the first thing I did was dd the whole 500gb onto a 1tb external drive which I'm now working on from on a different machine.

My sudo fdisk -l looks like this.

```

sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077146

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   970483711   485240832   83  Linux
/dev/sdb2       970485758   976771071     3142657    5  Extended
/dev/sdb5       970485760   976771071     3142656   82  Linux swap / Solaris

```

Could someone advise what my next step would be? I've just started running testdisk so I'll post the results when I get them.

Also, if I partition the unallocated 500gb from my 1tb drive as a (hopeful) recovery target area would that affect the image I've just dd'd over?

Many thanks,

---

### Post by raja.genupula on 2012-10-20
hi read this
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by megsona on 2012-10-20
Thanks Raja, I'll give parted rescue a try if testdisk doesn't work.

---

### Post by megsona on 2012-10-24
So, I've tried a few things now, with little success I'm afraid.

My first 'quick scan' in testdisk produced this,

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>* Linux                    0   1  1  1823 254 63   29302497
 P Linux Swap           60072   0  1 60800 254 63   11711385










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 15 GB / 13 GiB

```

Which looked as though it had found my original 15gb OS partition but nothing else other than my swap, no /home partition in between them.

At that point I went for the 'deep scan' option which produced this,

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>D Linux                    0   1  1  1823 254 62   29302496
 D Linux                    0  32 33 60409 208 23  970481664
 D Linux                 1824   2  1 60070 254 62  935737928
 D Linux Swap           60072   0  1 60800 254 46   11711368
 D Linux Swap           60409 240 56 60801  47 30    6285296







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 15 GB / 13 GiB

```

This looked much more hopeful since the third listed item

```
 D Linux                 1824   2  1 60070 254 62  935737928
```

is actually the right size, 479gb (multiplying the sectors by 512).

However when I hit 'p' to list the files I was dismayed to find the directory empty.

I've since tried parted rescue which didn't seem to find/do anything unless I'm using it wrong.

Also tried gpart which gave me this output,

```
Begin scan...
Possible partition(Windows NT/W2K FS), size(0mb), offset(61822mb)
Possible partition(Linux swap), size(5718mb), offset(471219mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(Linux swap or Solaris/x86): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 0mb #s(1) s(126612864-126612864)
   chs:  (1023/254/63)-(1023/254/63)d (7881/73/1)-(7881/73/1)r

Primary partition(2)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 5718mb #s(11711384) s(965056680-976768063)
   chs:  (1023/254/63)-(1023/254/63)d (60072/0/1)-(60800/254/62)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```

I'm not too sure what to make of that to be honest but it doesn't look very promising.

I feel sure that since my original /home partition started above 15gb and the new installation files of Quantal would be way below 15gb that my partition must be intact. I'm just not sure how to restore it. Also, I have way too much on it to start thinking about carving it...

I'm in the process of dd'ing a fresh copy from my original drive again since I had messed about with it quite a bit.

Any help would be most appreciated.

---

### Post by dino99 on 2012-10-24
[http://askubuntu.com/questions/43779/is-it-possible-to-unformat-an-ext4-partition-that-previously-had-an-ext4-partiti](http://askubuntu.com/questions/43779/is-it-possible-to-unformat-an-ext4-partition-that-previously-had-an-ext4-partiti)

---

### Post by oldfred on 2012-10-24
When you do a default install, it creates just / & swap. And the files in / may be anywhere within the / partition not necessarily at the beginning. We see issues with grub on very large drives where some boot files are at beginning of drive and others near end of drive. Bootinfoscript shows boot files locations.

If important parts of old /home got overwritten then it may not be recoverable by testdisk. Then the only choice is photorec or equivalents that just scan drive for anything that looks like a file and saves it to another drive.  I have used it. It takes a very long time as it has to scan entire drive looking for anything like a file and then writing to new location. It also does not recover filename, but just extension or filetype. It took me forever to sort thru files to rename. It also recovered for me all the old deleted copies as my disk was not very full and old copies were still there also. Never was sure I recovered last saved version of some files but got most back with lots of effort. Or oldfred now backs up more often.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by megsona on 2012-10-24
Thanks for all your replies, it looks like I'll be doing quite a bit of photorec/scalpel/cleanup work...

I'll have a look at the bootinfoscript and if I have any success I'll be sure to document it here.

Thanks,

---

### Post by since on 2012-10-24
try


```
dd
```

---

