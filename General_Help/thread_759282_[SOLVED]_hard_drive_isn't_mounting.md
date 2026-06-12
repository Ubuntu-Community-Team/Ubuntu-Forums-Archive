---
title: "[SOLVED] hard drive isn't mounting"
date: 2008-04-18
forum: General Help
---

### Post by nonewmsgs on 2008-04-18
this was working but i noticed it wasn't under "media" after a reboot.

fstab
```

# /dev/sda1
UUID=dd1cb74a-e953-4b38-af2e-66c49384e827 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fd346820-4f65-4f05-91aa-16b7b42402da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /home ext3 nodev,nosuid 0 2
/dev/hdb1 /home/william/newdrive1 ext3 rw,defaults,uid=1000 0 0


```

not mounting
```

william@jesus:~$ sudo fsck /dev/hdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/hdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes
 
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information
 
/dev/hdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hdb1: 157053/19546112 files (0.3% non-contiguous), 3469472/39072080 blocks
william@jesus:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
william@jesus:~$ dmesg | tail
[  108.140982] usb 4-2: not running at top speed; connect to a high speed hub
[  108.163067] usb 4-2: configuration #1 chosen from 1 choice
[  108.167017] hub 4-2:1.0: USB hub found
[  108.169928] hub 4-2:1.0: 4 ports detected
[  180.663920] scsi: unknown opcode 0xe9
[  180.663935] scsi: unknown opcode 0xed
[  185.641529] scsi: unknown opcode 0xf5
[  443.824553] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
[  814.676201] scsi: unknown opcode 0xeb
[  815.566086] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
william@jesus:~$ sudo fsck /dev/hdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/hdb1: clean, 157053/19546112 files, 3469472/39072080 blocks

```

---

### Post by pointone on 2008-04-18
```
EXT3-fs: Unrecognized mount option "uid=1000" or missing value
```

```
man 8 mount
```

"uid" does not appear to be a valid mount option for **ext3** filesystems. Try removing it from your fstab.

---

### Post by nonewmsgs on 2008-04-19
thanks - that totally worked!

 i just don't understand how it was fine with uid=1000 last time i mounted it....

---

