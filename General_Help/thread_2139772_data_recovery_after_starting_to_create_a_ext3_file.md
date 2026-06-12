---
title: "data recovery after starting to create a ext3 file system"
date: 2013-04-27
forum: General Help
---

### Post by ben22 on 2013-04-27
Hi,

I have an encrypted 2TB HDD with existing data on it. When opening it via command line, I made the mistake to create a new file system on it (obviously I was not thinking, but just following a tutorial ...), but stopped it in the process, when I recognized that this was a stupid idea. 

I researched and think I should make a) an image of the HD, b) try to repair the file system to recover data.

What do you suggest to recover / access the data?


I performed the following steps

> 
$cryptsetup luksOpen /dev/sdb superHD
$ sudo mkfs.ext3 -j -m 1 -O dir_index,filetype,sparse_super /dev/mapper/superHD  ---- THE ERROR
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488378389 blocks
4883783 blocks (1.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Writing inode tables: 1092/14905



Fortunately, I recognized at some point that creating a filesystem on an existing file system is a stupid idea. When I now try to mount, I get this error:
> 
$ sudo mount -t ext3 /dev/mapper/superHD /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/superHD,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What do you suggest to recover / access the data?

Thx,
ben

---

### Post by dcstar on 2013-04-27
Use the **testdisk** package.

---

