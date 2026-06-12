---
title: "Windows Softraid is building but not mounting... :/"
date: 2015-06-13
forum: General Help
---

### Post by aronwalker on 2015-06-13
Hi there

I'm trying to mount a windows softraid on my computer

I followed [This Guide]("http://ubuntuforums.org/showthread.php?t=833653") and I managed to build my array. However, when I try to mount it, I get the following error:

```

awalker@aaron-pc ~$ sudo mount /dev/md0 /mnt/raid
sudo password for awalker: 
ntfs_mst_post_read_fixup_warn: magic: 0x80018000  size: 1024   usa_ofs: 32770  usa_count: 32770: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x82018200  size: 1024   usa_ofs: 33282  usa_count: 33282: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x84018400  size: 1024   usa_ofs: 33794  usa_count: 33794: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x86018600  size: 1024   usa_ofs: 34306  usa_count: 34306: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x88018800  size: 1024   usa_ofs: 34818  usa_count: 34818: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x8a018a00  size: 1024   usa_ofs: 35330  usa_count: 35330: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x8c018c00  size: 1024   usa_ofs: 35842  usa_count: 35842: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x8e018e00  size: 1024   usa_ofs: 36354  usa_count: 36354: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x90019000  size: 1024   usa_ofs: 36866  usa_count: 36866: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x92019200  size: 1024   usa_ofs: 37378  usa_count: 37378: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x94019400  size: 1024   usa_ofs: 37890  usa_count: 37890: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x96019600  size: 1024   usa_ofs: 38402  usa_count: 38402: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x98019800  size: 1024   usa_ofs: 38914  usa_count: 38914: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x9a019a00  size: 1024   usa_ofs: 39426  usa_count: 39426: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x9c019c00  size: 1024   usa_ofs: 39938  usa_count: 39938: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x9e019e00  size: 1024   usa_ofs: 40450  usa_count: 40450: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xa001a000  size: 1024   usa_ofs: 40962  usa_count: 40962: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xa201a200  size: 1024   usa_ofs: 41474  usa_count: 41474: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xa401a400  size: 1024   usa_ofs: 41986  usa_count: 41986: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xa601a600  size: 1024   usa_ofs: 42498  usa_count: 42498: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xa801a800  size: 1024   usa_ofs: 43010  usa_count: 43010: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xaa01aa00  size: 1024   usa_ofs: 43522  usa_count: 43522: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xac01ac00  size: 1024   usa_ofs: 44034  usa_count: 44034: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xae01ae00  size: 1024   usa_ofs: 44546  usa_count: 44546: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb001b000  size: 1024   usa_ofs: 45058  usa_count: 45058: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb201b200  size: 1024   usa_ofs: 45570  usa_count: 45570: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb401b400  size: 1024   usa_ofs: 46082  usa_count: 46082: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb601b600  size: 1024   usa_ofs: 46594  usa_count: 46594: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xb801b800  size: 1024   usa_ofs: 47106  usa_count: 47106: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xba01ba00  size: 1024   usa_ofs: 47618  usa_count: 47618: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xbc01bc00  size: 1024   usa_ofs: 48130  usa_count: 48130: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xbe01be00  size: 1024   usa_ofs: 48642  usa_count: 48642: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xc001c000  size: 1024   usa_ofs: 49154  usa_count: 49154: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xc201c200  size: 1024   usa_ofs: 49666  usa_count: 49666: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xc401c400  size: 1024   usa_ofs: 50178  usa_count: 50178: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xc601c600  size: 1024   usa_ofs: 50690  usa_count: 50690: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xc801c800  size: 1024   usa_ofs: 51202  usa_count: 51202: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xca01ca00  size: 1024   usa_ofs: 51714  usa_count: 51714: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xcc01cc00  size: 1024   usa_ofs: 52226  usa_count: 52226: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xce01ce00  size: 1024   usa_ofs: 52738  usa_count: 52738: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xd001d000  size: 1024   usa_ofs: 53250  usa_count: 53250: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xd201d200  size: 1024   usa_ofs: 53762  usa_count: 53762: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xd401d400  size: 1024   usa_ofs: 54274  usa_count: 54274: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xd601d600  size: 1024   usa_ofs: 54786  usa_count: 54786: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xd801d800  size: 1024   usa_ofs: 55298  usa_count: 55298: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xda01da00  size: 1024   usa_ofs: 55810  usa_count: 55810: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xdc01dc00  size: 1024   usa_ofs: 56322  usa_count: 56322: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xde01de00  size: 1024   usa_ofs: 56834  usa_count: 56834: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe001e000  size: 1024   usa_ofs: 57346  usa_count: 57346: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe201e200  size: 1024   usa_ofs: 57858  usa_count: 57858: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe401e400  size: 1024   usa_ofs: 58370  usa_count: 58370: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe601e600  size: 1024   usa_ofs: 58882  usa_count: 58882: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xe801e800  size: 1024   usa_ofs: 59394  usa_count: 59394: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xea01ea00  size: 1024   usa_ofs: 59906  usa_count: 59906: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xec01ec00  size: 1024   usa_ofs: 60418  usa_count: 60418: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xee01ee00  size: 1024   usa_ofs: 60930  usa_count: 60930: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xf001f000  size: 1024   usa_ofs: 61442  usa_count: 61442: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xf201f200  size: 1024   usa_ofs: 61954  usa_count: 61954: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xf401f400  size: 1024   usa_ofs: 62466  usa_count: 62466: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xf601f600  size: 1024   usa_ofs: 62978  usa_count: 62978: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xf801f800  size: 1024   usa_ofs: 63490  usa_count: 63490: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xfa01fa00  size: 1024   usa_ofs: 64002  usa_count: 64002: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xfc01fc00  size: 1024   usa_ofs: 64514  usa_count: 64514: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xfe01fe00  size: 1024   usa_ofs: 65026  usa_count: 65026: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

The commands I used are as follows 

```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
sudo mkdir /mnt/raid 
sudo mount /dev/md0 /mnt/raid

```

I am using 4 Disks (WD 750GB) and am using Fedora 22 (I'm really really really sorry please forgive me)

They is nothing wrong with the array, as it still works under windows

When the error says " mount a different device under the /dev/mapper/ directory " - I dont know what this means - I am using MDADM rather than dmraid

Result of "cat /proc/partitions"
```

[awalker@aaron-pc ~]$ cat /proc/partitions
major minor  #blocks  name

   8        0  732574584 sda
   8        1  732571648 sda1
   8       16  976762584 sdb
   8       17     358400 sdb1
   8       18  500948992 sdb2
   8       19     460800 sdb3
   8       21     512000 sdb5
   8       22  469763072 sdb6
   8       32  732574584 sdc
   8       33  732571648 sdc1
   8       48  732574584 sdd
   8       49  732571648 sdd1
   8       64  732574584 sde
   8       65  732571648 sde1
 253        0    8384512 dm-0
 253        1  461373440 dm-1
   9        0 2930286592 md0

```

Contents of /dev/mapper

```

[awalker@aaron-pc ~]$ ls /dev/mapper
control  fedora-root  fedora-swap

```

Any Help would be amazing :)

Aaron

[EDIT] In the tutorial, it tells you to split the windows chunk size by the number of disks you have, as I have 4, I changed my chunk size to 32k to each disk. I got a different error (the same gobbildy gook as about post read was still there)
```
$MFTMirr error: Incomplete multi sector transfer detected in 'mft record'.
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by aronwalker on 2015-06-15
bumpity boo

---

### Post by aronwalker on 2015-06-18
Any one?

---

