---
title: "HDD isn't mounting (wrong fs type, bad option, bad superblock...)"
date: 2015-11-28
forum: General Help
---

### Post by MinasFilm on 2015-11-28
I have the HDD WD scorpio 250GB (wd2500bevt).
HDD has two partition: main with xubuntu 12.04 (ext3) and swop-partition.
Since some time OS xubuntu has showed me errors of GRUB, and when I tried to mount HDD through the USB-adapter to the other PC, I have got this:
```
~$ sudo mount /dev/sdb1 /mnt -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       &#1042; &#1085;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1093; &#1089;&#1083;&#1091;&#1095;&#1072;&#1103;&#1093; &#1087;&#1086;&#1083;&#1077;&#1079;&#1085;&#1072;&#1103; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103; &#1084;&#1086;&#1078;&#1077;&#1090; &#1073;&#1099;&#1090;&#1100;
       &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;&#1072; &#1074; syslog - &#1087;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1081;&#1090;&#1077; dmesg | tail &#1080;&#1083;&#1080; &#1095;&#1090;&#1086;-&#1090;&#1086;
       &#1074; &#1101;&#1090;&#1086;&#1084; &#1088;&#1086;&#1076;&#1077;
```
I checked the position of superblock-backups - ```

~$ sudo mke2fs -n /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
&#1052;&#1077;&#1090;&#1082;&#1072; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;&#1086;&#1081; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1099;=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
14753792 inodes, 59001848 blocks
2950092 blocks (5.00%) reserved for the super user
&#1055;&#1077;&#1088;&#1074;&#1099;&#1081; &#1073;&#1083;&#1086;&#1082; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093;=0
Maximum filesystem blocks=4294967296
1801 block groups
32768 blocks per group, 32768 fragments per group
8192 inod'&#1086;&#1074; &#1074; &#1075;&#1088;&#1091;&#1087;&#1087;&#1077;
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872
```
and tried to repair superblock from his first backup:
```
:~$ sudo e2fsck -f -b 32768 -y  /dev/sdb1
```
then I have tried to mount HDD again and got the same error message (wrong fs type, bad option, bad superblock...)

What else can I try to repair my HDD?

---

