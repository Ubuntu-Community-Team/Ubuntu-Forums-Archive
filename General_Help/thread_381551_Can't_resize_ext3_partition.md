---
title: "Can't resize ext3 partition"
date: 2007-03-11
forum: General Help
---

### Post by disturbedite on 2007-03-11
kubuntu 7.04 herd 5 i386
kernel 2.6.20-9
parted-1.7.1-3ubuntu4
qtparted-0.4.5-2ubuntu12
gparted-0.2.5-2ubuntu2
300GB sata 3.0 [sda1]
1st partition:  ext3@~296GBs
2nd partition: free@1.8GBs (created by me upon install of kubuntu)

i tried to resize two partitions on a secondary hdd i use for storage into one with qtparted but it wouldn't let me.

so then i tried it with gparted.  (i like it and it's gui better than qtparted).  i got this when i tried it with gparted:
```
GParted 0.2.5

Resize /dev/sda1 from 296.29 GiB to 298.09 GiB    ( ERROR )
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( ERROR )
e2fsck -f -y -v /dev/sda1
      
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found. Create? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

 73157 inodes used (0.19%)
 5992 non-contiguous inodes (8.2%)
 # of inodes with ind/dind/tind blocks: 56691/3824/5
66550013 blocks used (85.68%)
 0 bad blocks
 12 large files

 64332 regular files
 8815 directories
 0 character device files
 0 block device files
 0 fifos
 0 links
 0 symbolic links (0 fast symbolic links)
 0 sockets
--------
 73147 files
 
  e2fsck 1.40-WIP (14-Nov-2006)
```i think the "/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****" comment is the important one.  does it look to anyone that this is this the thing that is preventing me from resizing it?
p.s.  all my data is ok.  it didn't change anything since e2fsck was only running a check before gparted did anything.

---

### Post by dcstar on 2007-03-11
> **disturbedite said:**
> kubuntu 7.04 herd 5 i386
kernel 2.6.20-9
parted-1.7.1-3ubuntu4
qtparted-0.4.5-2ubuntu12
gparted-0.2.5-2ubuntu2
300GB sata 3.0 [sda1]
1st partition:  ext3@~296GBs
2nd partition: free@1.8GBs (created by me upon install of kubuntu)

i tried to resize two partitions on a secondary hdd i use for storage into one with qtparted but it wouldn't let me.
.........

Make sure anything that automounts drive/partitions is turned off when doing these things, it can cause all sorts of problems.

And also make sure that the partitions are unmounted.

---

### Post by disturbedite on 2007-03-11
> **dcstar said:**
> Make sure anything that automounts drive/partitions is turned off when doing these things, it can cause all sorts of problems.

And also make sure that the partitions are unmounted.

i don't know of anything i have that automounts and my partitions are unmounted.

---

