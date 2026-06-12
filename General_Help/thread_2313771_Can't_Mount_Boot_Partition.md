---
title: "Can't Mount Boot Partition"
date: 2016-02-15
forum: General Help
---

### Post by Enoch_Tsang on 2016-02-15
I mounted my boot partition /dev/sdb3 so I could edit my refind.conf file, no problem. The changes were made and I got onto ubuntu again. Then I realized there was something else I wanted to change in my refind.conf as well. 

Using the same command `sudo mount /dev/sdb3 /mnt`, this time there was an error that I needed to specify the file system type. So I used `sudo mount /dev/sdb3 /mnt -t auto`, same error. I used `sudo fsck /dev/sdb3` and i get the output:

```

fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb3


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device> 
```

This is quite alarming since this is my boot drive. I tried restarting my computer to see if I could still boot (stupidly brave I know) and it had no problems.
In linux, I tried both e2fsck suggested commands with a similar error. I ran `sudo mke2fs -n /dev/sdb3` and I got the output:

```

mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
32768 inodes, 131072 blocks
6553 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
16 block groups
8192 blocks per group, 8192 fragments per group
2048 inodes per group
Superblock backups stored on blocks: 
    8193, 24577, 40961, 57345, 73729 
```

I used the e2fsck with all those block numbers with the same error. 

Additionally, I also tried checking the filesystem type but it wasn't listed, sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL gave me:

```

NAME   FSTYPE   SIZE MOUNTPOINT                    LABEL
sda           931.5G                               
&#9492;&#9472;sda1 ntfs   931.5G /media/enoch/C47ABD537ABD434A 
sdb           232.9G                               
&#9500;&#9472;sdb1 ntfs     300M                               Windows RE tools
&#9500;&#9472;sdb2 vfat     260M                               SYSTEM
&#9500;&#9472;sdb3          128M                               
&#9500;&#9472;sdb4 ntfs   117.7G                               Windows
&#9500;&#9472;sdb5 ext4    18.6G /                             
&#9500;&#9472;sdb6 ext4    74.5G /home                         
&#9492;&#9472;sdb7 swap    21.4G [SWAP] 
```

Any help on what I should do? It seems to still be booting fine (I only tried it once) but this seems like a problem that could kick me in the ass later, and I still want to alter my refind.conf a little bit.

---

### Post by yancek on 2016-02-15
Sometimes mounting without specifiying the filesystem type doesn't work and the message you report just means you need to do that since it wasn't able to determine the filesystem for whatever reason.  So you simply need to specifiy it and auto isn't a filesystem type, that was already done with your original command and didn't work.  This is a boot partition for which system, windows or Ubuntu.  What's on sdb2, is that an EFI partition?  If you are using rEfind I expect it is and thus probably vfat filesystem.  You could try parted -l command to see if it shows the fs type.

---

### Post by Bucky Ball on 2016-02-15
Can we assume you are using a Mac?

---

