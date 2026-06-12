---
title: "Problem running e2fsck on a newly expanded raid5"
date: 2013-11-24
forum: General Help
---

### Post by Clongetty on 2013-11-24
Hi,

I have a ubuntu server running a software raid5.

I had 4x1TB hard drives and I replaced them one by one by 4x3tb drives. Each time I replaced a disk I resynchronised the parity and ran a e2fsck check (sudo e2fsck -c -f /dev/md0) so far everything went fine.

Then once all the 4 drives were replaced I expanded the partition so it uses all the available storage. 
Since then, the partition is working fine I can access it and see my whole 8.05tb and can use them, but when I try to run a final e2fsck scan I get an error and it doesn't run the full scan that usualy takes a couple of hours "badblocks: invalid option -- '2'"
Here you can see the full message : 
> steel@NAS:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[5] sdc1[6] sde1[4] sdd1[7]
      8790792192 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
unused devices: <none>

steel@NAS:~$ sudo e2fsck -c -f /dev/md0
e2fsck 1.41.14 (22-Dec-2010)
**badblocks: invalid option -- '2'**
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]
/dev/md0: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: ***** FILE SYSTEM WAS MODIFIED *****
/dev/md0: 73668/549429248 files (2.3% non-contiguous), 711829345/2197698048 blocks

Is it safe to ignore this and still use this raid for storage?

---

### Post by Clongetty on 2013-11-24
I think I have found the problem,

I realised that -c in e2fsck ran the badblocks command.
I ran it seperately and got this error :
> steel@NAS:~$ sudo badblocks -s /dev/md0
badblocks: File too large while trying to determine device size


Now im trying to update my softwares to see if it's corrected in a newer version.

---

### Post by Clongetty on 2013-11-24
After updating my softwares everything is now working fine! 

> steel@NAS:~$ sudo e2fsck -c -f /dev/md0e2fsck 1.42 (29-Nov-2011)
Checking for bad blocks (read-only test):   0.02% done, 0:13 elapsed. (0/0/0 errors)


---

