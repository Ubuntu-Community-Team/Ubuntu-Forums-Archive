---
title: "external usb will not mount"
date: 2013-06-12
forum: General Help
---

### Post by qwertyjjj on 2013-06-12
computer crashed and now the external usb won't mount.
i tried repairing but it still doesn't work:

> 
hh@spain ~ $ mount /dev/sdc /mnt/temp
mount: only root can do that
hh@spain ~ $ sudo mount /dev/sdc /mnt/temp
[sudo] password for hh: 
mount: mount point /mnt/temp does not exist
hh@spain ~ $ mkdir /mnt/temp
mkdir: cannot create directory `/mnt/temp': Permission denied
hh@spain ~ $ sudo mkdir /mnt/temp
hh@spain ~ $ sudo mount /dev/sdc /mnt/temp
mount: you must specify the filesystem type
hh@spain ~ $ sudo mount /dev/sdc /mnt/temp -t ext2
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

hh@spain ~ $ dumpe2fs /dev/sdc | grep superblock
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Permission denied while trying to open /dev/sdc
Couldn't find valid filesystem superblock.
hh@spain ~ $ sudo dumpe2fs /dev/sdc | grep superblock
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdc
Couldn't find valid filesystem superblock.
hh@spain ~ $ mke2fs /dev/hda
mke2fs 1.42.5 (29-Jul-2012)
Could not stat /dev/hda --- No such file or directory

The device apparently does not exist; did you specify it correctly?
hh@spain ~ $ mke2fs /dev/sdc
mke2fs 1.42.5 (29-Jul-2012)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
mke2fs: Permission denied while trying to determine filesystem size
hh@spain ~ $ sudo mke2fs /dev/sdc
mke2fs 1.42.5 (29-Jul-2012)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 inodes, 122096646 blocks
6104832 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Allocating group tables: done                            
Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done     

hh@spain ~ $ sudo fsck -b 32768 /dev/sdc
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sdc was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdc: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdc: 11/30531584 files (0.0% non-contiguous), 1934134/122096646 blocks
hh@spain ~ $ sudo mount /dev/sdc /mnt/temp
hh@spain ~ $ cd /mnt/temp
hh@spain /mnt/temp $ ls -l
ls: cannot access lost+found: Input/output error
total 0
d????????? ? ? ? ?            ? lost+found
hh@spain /mnt/temp $ cd lost+found
bash: cd: lost+found: Input/output error
hh@spain /mnt/temp $ cd lost*
bash: cd: lost+found: Input/output error
hh@spain /mnt/temp $ 



---

### Post by Vitsliputsli on 2013-06-14
Use mke2fs with -c to check for bad blocks, if information on disk is not important.

---

