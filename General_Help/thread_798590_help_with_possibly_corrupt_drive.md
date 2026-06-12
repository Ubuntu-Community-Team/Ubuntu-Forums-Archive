---
title: "help with possibly corrupt drive"
date: 2008-05-18
forum: General Help
---

### Post by supersonicdarky on 2008-05-18
This morning when i woke up, deluge had no torrents in it for some reason and had an error saying that cannot save xxx to a read only filesystem. So I close it, remount it as rw, start it, still no torrents in it. Then a few minutes later the error shows up again. I then decide to restart. Same thing happens afterwards. I reinstall deluge, no help. I then decide to take a look at dmesg, and I see this:

```
[  612.982313] FAT: Filesystem panic (dev sdb1)
[  612.982314]     clusters badly computed (2777 != 2775)
[  612.982481] FAT: Filesystem panic (dev sdb1)
[  612.982483]     clusters badly computed (2778 != 2776)
[  612.982651] FAT: Filesystem panic (dev sdb1)
[  612.982652]     clusters badly computed (2779 != 2777)
[  612.982818] FAT: Filesystem panic (dev sdb1)
[  612.982820]     clusters badly computed (2780 != 2778)
[  612.982989] FAT: Filesystem panic (dev sdb1)
[  612.982990]     clusters badly computed (2781 != 2779)
[  612.983158] FAT: Filesystem panic (dev sdb1)
[  612.983159]     clusters badly computed (2782 != 2780)
[  612.983321] FAT: Filesystem panic (dev sdb1)
[  612.983323]     clusters badly computed (2783 != 2781)
[  612.983489] FAT: Filesystem panic (dev sdb1)
[  612.983490]     clusters badly computed (2784 != 2782)
[  612.983658] FAT: Filesystem panic (dev sdb1)
[  612.983659]     clusters badly computed (2785 != 2783)
[  612.983827] FAT: Filesystem panic (dev sdb1)
[  612.983828]     clusters badly computed (2786 != 2784)
[  612.984000] FAT: Filesystem panic (dev sdb1)
[  612.984002]     clusters badly computed (2787 != 2785)
[  612.984172] FAT: Filesystem panic (dev sdb1)
[  612.984174]     clusters badly computed (2788 != 2786)
[  612.984340] FAT: Filesystem panic (dev sdb1)
[  612.984341]     clusters badly computed (2789 != 2787)
[  612.984505] FAT: Filesystem panic (dev sdb1)
[  612.984506]     clusters badly computed (2790 != 2788)
[  612.984685] FAT: Filesystem panic (dev sdb1)
[  612.984686]     clusters badly computed (2791 != 2789)
[  612.984849] FAT: Filesystem panic (dev sdb1)
[  612.984851]     clusters badly computed (2792 != 2790)
[  612.985022] FAT: Filesystem panic (dev sdb1)
[  612.985024]     clusters badly computed (2793 != 2791)
[  612.985195] FAT: Filesystem panic (dev sdb1)
[  612.985196]     clusters badly computed (2794 != 2792)
[  612.985364] FAT: Filesystem panic (dev sdb1)
[  612.985366]     clusters badly computed (2795 != 2793)
[  612.985530] FAT: Filesystem panic (dev sdb1)
[  612.985531]     clusters badly computed (2796 != 2794)
[  612.985696] FAT: Filesystem panic (dev sdb1)
[  612.985697]     clusters badly computed (2797 != 2795)
[  612.985865] FAT: Filesystem panic (dev sdb1)
[  612.985867]     clusters badly computed (2798 != 2796)
[  612.986030] FAT: Filesystem panic (dev sdb1)
[  612.986031]     clusters badly computed (2799 != 2797)
[  612.986191] FAT: Filesystem panic (dev sdb1)
[  612.986192]     clusters badly computed (2800 != 2798)
[  612.986355] FAT: Filesystem panic (dev sdb1)
[  612.986356]     clusters badly computed (2801 != 2799)
[  613.503987] FAT: Filesystem panic (dev sdb1)
[  613.503993]     clusters badly computed (2802 != 2800)

```
Like that, except a lot more. I start getting worried, decide to find out how to fsck the drive, find [this](http://linux.die.net/man/8/fsck.vfat) page. After reading a bit, I try:
```
sudo dosfsck -a /dev/sdb1
```
Then it returns:
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Wrong checksum for long file name "01 :7ii1:8fn:300:5Fa:6op:33P:32a:32h:33y:32w:56D:7rG:68G.ogg".
  (Short name 000\0000000.\000GG may have changed without updating the long name)
  Not auto-correcting this.
Wrong checksum for long file name "02 :7ii2:8fn:300:31-:32J:31g:31d:9Aj:6vl.ogg".
  (Short name 001\0000000.\000GG may have changed without updating the long name)
  Not auto-correcting this.
/Music/OST/Clannad/Drama CD CLANNAD Hikari Mimamoru Sakamichi de/Drama CD CLANNAD Hikari Mimamoru Sakamichi de Vol. 4/Disc 1/01 :7ii1:8fn:300:5Fa:6op:33P:32a:32h:33y:32w:56D:7rG:68G.ogg
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000GG
/Music/OST/Clannad/Drama CD CLANNAD Hikari Mimamoru Sakamichi de/Drama CD CLANNAD Hikari Mimamoru Sakamichi de Vol. 4/Disc 1/02 :7ii2:8fn:300:31-:32J:31g:31d:9Aj:6vl.ogg
  Bad file name.
  Auto-renaming it.
  Renamed to 001\0000000.\000GG
Wrong checksum for long file name "02 :33f:32u:32g:33H:33y:338:300:5Fa:6op:31L:32J:31X.ogg".
  (Short name 000\0000000.\000GG may have changed without updating the long name)
  Not auto-correcting this.
Wrong checksum for long file name "04 :33f:32u:32g:33H:33y:338:300:5T2:4uA:31L:32J:31X.ogg".
  (Short name 001\0000000.\000GG may have changed without updating the long name)
  Not auto-correcting this.
/Music/OST/Clannad/Furukawa Sanchi ~Heion Naru Furukawa-pan no Ichijitsu~/02 :33f:32u:32g:33H:33y:338:300:5Fa:6op:31L:32J:31X.ogg
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000GG
/Music/OST/Clannad/Furukawa Sanchi ~Heion Naru Furukawa-pan no Ichijitsu~/04 :33f:32u:32g:33H:33y:338:300:5T2:4uA:31L:32J:31X.ogg
  Bad file name.
  Auto-renaming it.
  Renamed to 001\0000000.\000GG
Free cluster summary wrong (3793030 vs. really 3793034)
  Auto-correcting.
Performing changes.
/dev/sdb1: 28060 files, 11465240/15258274 clusters

```
Now even though it says it fixed it, if I run again, it shows the same things. What should I do next? It's a 500gb drive and I don't have nearly enough space to back everything up.

Please and thnx.

---

### Post by Monicker on 2008-05-18
The hard drive vendor should have a diagnoistics and repair utililty avaialable at their web site.  What is the brand and model number of the drive?

---

