---
title: "noob question: merging partitions?"
date: 2008-06-16
forum: General Help
---

### Post by laihafloyd on 2008-06-16
I installed ubuntu (now 8.04) but left the original windows partition in place.  since i no longer use windows, i would like to merge it into my linux partition.  is this possible or do i have to just have an empty drive for data files?  I've already deleted the partition using gparted and formated it to ext3 (my current root file system). 

If i can't merge them, can i locate the home directories on the new partition?  how would i do that?  thanks for any help,


marc

---

### Post by kalesh7 on 2008-06-16
you should be able to delete the old partition using gparted and then expand your ubuntu partition to fill the unused space.
for moving home directory (please doublecheck the commands as I am just typyng from memory)
1) backup home directory(/home) sudo mv /home /home.back
2) create folder /home sudo mkdir /home
3) mount new partition as home mount /dev/sda2 /home (replace sda2 with your partition
4) add to fstab

---

### Post by laihafloyd on 2008-06-17
i ran the live cd and used gparted to resize he root partition and it appeared to work until the very end.  i got an error during the disk check after the resize was done.  when i restarted, the root partition is the correct size, but all of the space that I gained is used space instead of free space.  i'm not sure why or where to go from here.  any idea?  thanks again.

---

### Post by laihafloyd on 2008-06-17
this is the error report...

GParted 0.3.5

Libparted 1.7.1

Grow /dev/sda3 from 15.35 GiB to 59.18 GiB  01:24:40    ( ERROR )
     	
calibrate /dev/sda3  00:00    ( SUCCES )
     	
path: /dev/sda3
start: 91923930
end: 124118189
size: 32194260 (15.35 GiB)
calculate new size and position of /dev/sda3  00:00    ( SUCCES )
     	
requested start: 0
requested end: 124118189
requested size: 124118190 (59.18 GiB)
new start: 63
new end: 124118189
new size: 124118127 (59.18 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  02:24    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

386327 inodes used (19.17%)
18603 non-contiguous inodes (4.8%)
# of inodes with ind/dind/tind blocks: 15010/212/0
2521713 blocks used (62.66%)
0 bad blocks
0 large files

319826 regular files
33719 directories
140 character device files
43 block device files
2 fifos
518 links
32578 symbolic links (29817 fast symbolic links)
10 sockets
--------
386836 files
e2fsck 1.40.8 (13-Mar-2008)
move partition to the left  00:00    ( SUCCES )
     	
old start: 91923930
old end: 124118189
old size: 32194260 (15.35 GiB)
new start: 63
new end: 32194322
new size: 32194260 (15.35 GiB)
move filesystem to the left  01:14:54    ( SUCCES )
     	
using internal algorithm
copy 32194260 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:05    ( SUCCES )
     	
32768 of 32768 copied
4.25762 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:04    ( SUCCES )
     	
32768 of 32768 copied
4.59975 seconds
optimal blocksize is 64 sectors (32.00 KiB)
copy 32128724 sectors using a blocksize of 64 sectors  01:14:45    ( SUCCES )
     	
32128724 of 32128724 copied
32194260 sectors copied
check filesystem on /dev/sda3 for errors and (if possible) fix them  02:27    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

386327 inodes used (19.17%)
18603 non-contiguous inodes (4.8%)
# of inodes with ind/dind/tind blocks: 15010/212/0
2521713 blocks used (62.66%)
0 bad blocks
0 large files

319826 regular files
33719 directories
140 character device files
43 block device files
2 fifos
518 links
32578 symbolic links (29817 fast symbolic links)
10 sockets
--------
386836 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
resize2fs /dev/sda3
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 4024282 blocks long. Nothing to do!

calculate new size and position of /dev/sda3  00:00    ( SUCCES )
     	
requested start: 63
requested end: 124118189
requested size: 124118127 (59.18 GiB)
new start: 63
new end: 124118189
new size: 124118127 (59.18 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  02:20    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

386327 inodes used (19.17%)
18603 non-contiguous inodes (4.8%)
# of inodes with ind/dind/tind blocks: 15010/212/0
2521713 blocks used (62.66%)
0 bad blocks
0 large files

319826 regular files
33719 directories
140 character device files
43 block device files
2 fifos
518 links
32578 symbolic links (29817 fast symbolic links)
10 sockets
--------
386836 files
e2fsck 1.40.8 (13-Mar-2008)
grow partition from 15.35 GiB to 59.18 GiB  00:05    ( SUCCES )
     	
old start: 63
old end: 32194322
old size: 32194260 (15.35 GiB)
new start: 63
new end: 124118189
new size: 124118127 (59.18 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  02:25    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

386327 inodes used (19.17%)
18603 non-contiguous inodes (4.8%)
# of inodes with ind/dind/tind blocks: 15010/212/0
2521713 blocks used (62.66%)
0 bad blocks
0 large files

319826 regular files
33719 directories
140 character device files
43 block device files
2 fifos
518 links
32578 symbolic links (29817 fast symbolic links)
10 sockets
--------
386836 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:05    ( ERROR )
     	
resize2fs /dev/sda3
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/sda3' first.


========================================

---

### Post by kalesh7 on 2008-06-17
hmm that seems strange can you dig down folders from / looking for an extra large folder (in GB) or your windows files? maybe you just need to delete it?

---

### Post by laihafloyd on 2008-06-21
can't find any files that would have taken up 50 gigs during the expand.  not sure where to go from here.

---

### Post by geirha on 2008-06-21
What does ```
sudo fdisk -l
``` run in a terminal say?

---

### Post by laihafloyd on 2008-06-21
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00df00df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            7727        9665    15575017+   5  Extended
/dev/sda3               1        7726    62059063+  83  Linux
/dev/sda5            7817        7880      514017   82  Linux swap / Solaris
/dev/sda6            7881        9665    14337981   83  Linux
/dev/sda7            7727        7816      722862   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by geirha on 2008-06-21
The partition table looks good, reports about 60 gigs. This should report the size as around 60G too
```
df -h /dev/sda3
```

If it doesn't, boot your ubuntu cd ( or gparted cd if you don't have your ubuntu cd at hand), and run
```
sudo e2fsck -f /dev/sda3
sudo resize2fs /dev/sda3
```

Paste the output if it fails. If it succeeds, you should see some more free space on your root filesystem when you boot back into your ubuntu system.

---

### Post by laihafloyd on 2008-06-21
df -h /dev/sda3 displays

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              16G  9.0G  5.5G  63% /

why is this different than the output of fdisk -l?

---

### Post by unutbu on 2008-06-21
Think of a partition as a room. 
Think of a filesystem as a filing cabinet inside the room. 

Most often the filesystem is made to fit the partition, like a filing cabinet that fills up a room.

In your case, you have a filesystem that is much  smaller than your partition -- like a small filing cabinet in a big room.

df reports the size of your filesystem.
fdisk -l reports the size of your partition.

geirha's command
```
sudo resize2fs /dev/sda3

```
will resize the filesystem to the size of the partition.

---

### Post by laihafloyd on 2008-06-22
thanks for the reply - i tried doing the resize and couldn't get anything to work. 

i ended up copying my home directory onto my flash hard drive and started all over.  i used fdisk to delete each partition while running on my live cd and reinstalled ubuntu.  now i have all 80 gigs available (minus the swap partition.

thanks again for all of your relies,


Marc

---

