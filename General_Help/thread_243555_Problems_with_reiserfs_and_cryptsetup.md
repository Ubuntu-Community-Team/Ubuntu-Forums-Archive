---
title: "Problems with reiserfs and cryptsetup"
date: 2006-08-25
forum: General Help
---

### Post by sandoz on 2006-08-25
Hi,

I am in real trouble with my encrypted home-partition (reiserfs 3.6).
With out any visible reason just some days ago it couldn't be mounted again. The error message was (is):

```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/cryptohome,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

In the log file, there is a message like this
```
ReiserFS: dm-6: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on dm-6
```

During the last days I tried the following:
1. reiserfsck /dev/mapper/cryptohome
Result: bread: Cannot read the block (irgendeine Nummer): (Input/output error).
2. reiserfsck --rebuild-sb /dev/mapper/cryptohome
Result: It build the new superblock, but there were more errors found.
3. reiserfsck /dev/mapper/cryptohome
Result: Bad root block 0. (--rebuild-tree did not complete)
4. reiserfsck --rebuild-tree /dev/mapper/cryptohome
Result: After some time the command aborts.
5. /sbin/badblocks /dev/mapper/cryptohome
Result: No 'badblocks' found.

I search with grep on the mapper device
```
grep -b "eintextineinerdatei" /dev/mapper/cryptohome
```

and found my data. This means that decryption is working correctly.


But the file system is some how in disorder.

debugreiserfs says:
```
debugreiserfs 3.6.19 (2003 www.namesys.com)


Filesystem state: consistency is not checked after last mounting

Reiserfs super block in block 16 on 0xfe06 of format 3.6 with standard journal
Count of blocks on the device: 9767504
Number of bitmaps: 299
Blocksize: 4096
Free blocks (count of blocks - used [journal, bitmaps, data, reserved] blocks): 0
Root block: 0
Filesystem is NOT clean
Tree height: 0
Hash function used to sort names: not set
Objectid map size 0, max 972
Journal parameters:
        Device [0x0]
        Magic [0x0]
        Size 8193 blocks (including 1 for journal header) (first block 18)
        Max transaction length 1024 blocks
        Max batch size 900 blocks
        Max commit age 30
Blocks reserved by journal: 0
Fs state field: 0x1:
         some corruptions exist.
sb_version: 2
inode generation number: 0
UUID: cb3687c0-5c3f-4621-8c88-8d87de9016e0
LABEL:
Set flags in SB:

```

Does anybody have an idea, what to do?

Thanks,
sandoz

---

