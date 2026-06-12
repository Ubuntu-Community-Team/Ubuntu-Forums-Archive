---
title: "Is my drive shot?"
date: 2008-02-21
forum: General Help
---

### Post by Culito on 2008-02-21
Hi folks.
So I have a little hard drive I store some music on:

Disk /dev/hdb: 4310 MB, 4310433792 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdfe7cf0

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         523     4200966    b  W95 FAT32

I just recently upgraded and did a fresh install.  So I made a mount point:

/media/music

And tried to mount it:

sudo mount -t vfat /dev/hdb /media/music

I get this error:
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Dmesg | tail:
[21474.508000] FAT: bogus number of reserved sectors
[21474.508000] VFS: Can't find a valid FAT filesystem on dev hdb.

So...is my drive shot?

Thanks,
-C

---

### Post by tgalati4 on 2008-02-21
>sudo cfdisk /dev/hdb

Examine the partition information.  If it looks correct, then "Write" and quit to rewrite the partition table.  Reboot and you should be good until the next hiccup.

If that doesn't work, then:

>sudo fsck /dev/hdb

---

### Post by confused57 on 2008-02-21
You might also try:
```
sudo mount -t vfat /dev/hdb1 /media/music
```

after you've created the /media/music directory:
```
sudo mkdir /media/music
```

Added:  You could also try:
```
sudo mount /dev/hdb1 /media/music -t vfat -o umask=000
```

---

### Post by Culito on 2008-02-21
> **tgalati4 said:**
> >sudo cfdisk /dev/hdb

Examine the partition information.  If it looks correct, then "Write" and quit to rewrite the partition table.  Reboot and you should be good until the next hiccup.

If that doesn't work, then:

>sudo fsck /dev/hdb

Thanks.
I didn't go through with cfdisk because it said that I might lose all the info on the drive.  Is it likely that I'll lose all of my music?

fsck output:
 sudo fsck /dev/hdb
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by tgalati4 on 2008-02-21
It looks like the partition table is messed up.  If you rewrite the partition table with different values than how the drive is actually set up, then yes you will lose data.  If you rewrite the partition table with values that match how the drive is really set up, then Linux can see it and mount it correctly.  The fact that fsck can't recognize it is a good indication.

Cfdisk warns you of data loss because it's always possible, but I have safely recovered drives this way.  Simply rewrite the partition table and reboot.  You can perform an fsck afterward, although that will happen automatically during bootup.

---

### Post by Culito on 2008-02-23
So I tried Cfdisk and fsck to no avail.  Cfdisk writes the partition information, but the output of fsck shows the same error.
This part interests me:
"The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>"

Isn't ext2 different than FAT32?

---

### Post by confused57 on 2008-02-23
Here's how to run a filesystem check on a FAT32 partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_on_a_FAT32_](http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_on_a_FAT32_)

---

