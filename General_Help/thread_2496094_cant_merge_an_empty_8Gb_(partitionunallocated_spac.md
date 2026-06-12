---
title: "cant merge an empty 8Gb (partition/unallocated space) to root partition on right"
date: 2024-03-13
forum: General Help
---

### Post by prem18 on 2024-03-13
Hello friends,
i searched google and forums, but there seems to no one facing my exact scenario, and so need help.

my root partition filled up, and system did not boot.
so, i used a live cd and have gparted running on it now.

i shaved some space of my swap space, and so have 8gb of space.
I need to append it to the root partition but this is on the LEFT of the sda4 (root partition).

How do I MOVE it to the right of the sda4.

I have tried to create a new partition, but all other posts are not clear on how the move happens.

Please advise. TIA!!

---

### Post by yancek on 2024-03-14
It is not possible to make any realistic suggestions without more specific details about your system which you can post with the output of the command:  sudo fdisk -l
This will list information including partitions, their sizes,locations and sectors.  To expand a partition you need free space contiguous to it. To move or modify a partition in any way it needs to be unmounted

Common reasons for a / partition filling are having the partition too small to start with, installing too much software or putting too much data on a partition or very large log files.  What are you doing with GParted?  Did you go to the /var/log directory and delete large log files?  Did you use the find command to find the largest files and check to see if they are files you need?  Without more details, it will be just guessing.

---

### Post by TheFu on 2024-03-14
You can move some data out of the / partition into a new partition that will use the free space.  If your root, /,  partition is over 35GB in size, you really need to do this.  Keeping the OS separate from everything else is a good practice.  

If you are using a swapfile, not a swap partition, that would be an easy way to free some space.  Create a 4.1GB swap partition, then add it to the system and disable the swap file. After that is done, delete the swap file to gain that space to have more working room to do what needs to actually happen.  If you don't have /home/ in a separate partition - that would be the first thing to move out of /.  Next, I'd move /var/ to a separate partition.

And don't forget that cleaning up junk will often free TBs of data.  Have you deleted the _trash_ recently on all partitions?

BTW, as much as I had screen images, showing a gparted window with the drive+partitions in question really is the easy way to show the issues.  I'll deny I suggested this in the future, but it is true.  **fdisk** or **parted** output show the information too, but just not as clearly. ;(  **lsblk** can also show some good information.

A non-booting system means you really need to get better at keeping your disk use under check.

While it is possible to shift a partition left, this is extremely costly, since all the data will be copied left. Depending on the amount of data, that can take 2 days.

Anyway, you have lots of options.

Lastly, if you'd enabled LVM at install time, adding the free space to a logical volume where it was needed - left, right, discontinuous ... doesn't matter, is about 5 seconds and 1 command. Of course, LVM does add some complexity to storage management, so only you can decide if that extra complexity is worth the flexibility.

For example, I use LVM, 
```
NAME                 TYPE  FSTYPE         SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1              disk               931.5G                               
&#9500;&#9472;nvme0n1p1          part  ext2             1M                               
&#9500;&#9472;nvme0n1p2          part  vfat            50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3          part  ext4           700M  339.9M    42%                /boot
&#9492;&#9472;nvme0n1p4          part  LVM2_member  930.8G                               
  &#9500;&#9472;vg01-swap01      lvm   swap           4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01      lvm   ext4            35G   24.9G    22%                /
  &#9500;&#9472;vg01-var01       lvm   ext4            20G   12.9G    29%                /var
  &#9500;&#9472;vg01-tmp01       lvm   ext4             4G    3.6G     2% tmp01          /tmp
  &#9500;&#9472;vg01-home01      lvm   ext4            20G   10.1G    44% home01         /home
  &#9500;&#9472;vg01-libvirt--01 lvm   ext4           137G    2.8G    98% libvirt--01    /var/lib/libvirt
  &#9500;&#9472;vg01-lxd--containers--01
  &#9474;                  lvm                   30G                               
  &#9492;&#9472;vg01-ubuntu2310  lvm                   15G
```
The left column is a mix of partitions and logical volumes.  As you can see, I split up my allocations to be specific to the requirements.  All of my LVM is inside a single partition, nvme0n1p4. If you do the math, you can see I'm using about 250GB of a 1TB NVMe SSD.  Plenty of room.  Because of the flexibility of LVM, there are lots of options.  I don't keep "data" on SSD storage. The computer has 6 other internal HDDs with spinning disks inside it. That's where most data - many TBs worth - get placed.

Anyways, next time you install, you have some storage things to consider.

---

### Post by prem18 on 2024-03-15
thank you folks for the replies, I am a noob, and did something stupid where I wiped out the data! So, this thread is moot for me, but i will pay attention to above note when I am setting it up again.

---

### Post by TheFu on 2024-03-15
> **prem18 said:**
> thank you folks for the replies, I am a noob, and did something stupid where I wiped out the data! So, this thread is moot for me, but i will pay attention to above note when I am setting it up again.

I've done that a few times. 100% by accident and before I had backups that weren't so much hassle that I'd actually do them. ;)  BTW, backups were a huge hassle for me for about 10 yrs, even when I had a tape drive.

---

