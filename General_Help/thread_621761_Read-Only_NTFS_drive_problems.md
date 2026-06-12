---
title: "Read-Only NTFS drive problems"
date: 2007-11-24
forum: General Help
---

### Post by Thimetolive on 2007-11-24
Hi,

For some background info, I am new to Linux.

My major problem is I have read-only rights to a additional NTFS drive. 

I have determined the drive is at /dev/sdb by doing a fdisk but it shows up as "New Volume" under the computer file browser. After I mount "New Volume" I see a /media/New Volume but not a /dev/New Volume.

After reading a TON of posts on the problem I've come up with dead ends at every turn.

1. chmod doesnt work
2. ```
sudo mount /dev/sdb  /media/windows/ -t ntfs -o nls=utf8,umask=0222 
   wrong fs type, bad option, bad superblock on dev/sdb
   missing code page or other error
```
3. After adding /dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0    to fstab I get
      ```
wrong fs type, bad option, bad superblock on dev/sdb
      missing code page or other error
```
4.  dmesg | tail gives me this
    ```
 NTFS -fs error (device sdb) : read_ntfs_boot_sector(): Mount option errors=recover not used.
     Aborting without trying to recover.
```
5. fsck dev/sdb doesnt work
    ```
fsck.ntsf: not found
    Error 2 while executing fsck.ntsf for dev/sdb
```

There are a lot of other things Ive tried as well without success but these seemed to keep reappearing in several posts. Im hoping Im missing something obvious.

Thanks in advance for any suggestions!

---

### Post by ajmorris on 2007-11-24
hi there thimetolive,
This will most likely be because NTFS write support has not been enabled in your kernel.

I suggest installing ntfs-3G ```
sudo apt-get install ntfs-3g
```

then mounting your ntfs partition with it.```
ntfs-3g 'device' 'destination'
```
Then, if this works, you can add it to /etc/fstab
```
/dev/device             mount point      ntfs-3g         users           0 0
```

Hope this helps

---

### Post by stinger30au on 2007-11-24
i had the same drama in 7.04

go applications - >add remove

set the show tab in the upper right to - show all 

search on mount

scroll down till to you find storage device manager

install it

then go system ->administration > storage device manager

set the hdd up to automount with read/write then hit default to save the settings.
restart the pc. 
fixed

---

### Post by bingoUV on 2007-11-24
Please post output of fdisk -l

---

### Post by Thimetolive on 2007-11-24
> **ajmorris said:**
> hi there thimetolive,
This will most likely be because NTFS write support has not been enabled in your kernel.

I suggest installing ntfs-3G ```
sudo apt-get install ntfs-3g
```

then mounting your ntfs partition with it.```
ntfs-3g 'device' 'destination'
```
Then, if this works, you can add it to /etc/fstab
```
/dev/device             mount point      ntfs-3g         users           0 0
```

Hope this helps
. 

THANK YOU!!! After several hours of frustration, this finally did the trick. 
I did get an error message after following your instructions, but I rebooted into windows then shutdown and everything worked great!

Thanks for all the replies guys. Without this forum I would be forced to give up my experiment with Ubuntu.

---

