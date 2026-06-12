---
title: "After converting virtual disk from RAID1 to RAID0 fdisk sees space but mount doesn't"
date: 2014-05-03
forum: General Help
---

### Post by Nathaniel_Novod on 2014-05-03
Using Ubuntu 14.04, I had a virtual drive (two physical devices) as a hardware RAID1 configuration.  To convert it to a RAID0 drive I used MegaCli to delete the old logical drive and recreate it as RAID0, then I did a mkfs (-t ext3) to create a single ext3 partition and finally remounted the drive.  "fdisk -l" shows that the drive is now 4.0Tb as expected but the remounted filesystem, as shown by df, is still only 1.8Tb as it was before I did the RAID1 to RAID0 conversion.  mkfs seems to have only seen half the blocks now available.  Any ideas why?  Is there someplace else I have to poke in the OS?  An additional option I must give to mkfs?

Following are the commands used and responses.

Thank you for any help.

# umount /home/nnovod/data
# MegaCli -CfgLdDel -L1 -a0
                                     
Adapter 0: Deleted Virtual Drive-1(target id-1)
Failed while adding the configuration to OS.

Exit Code: 0x00

# MegaCli -CfgLdAdd -r0[252:2, 252:3] -a0
                                     
Adapter 0: Created VD 1

Adapter 0: Configured the Adapter!!

Exit Code: 0x00

# sudo fdisk -l

Disk /dev/sda: 239.5 GB, 239511535616 bytes
255 heads, 63 sectors/track, 29118 cylinders, total 467795968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000efbdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4096   447311871   223653888   83  Linux
/dev/sda2       447311872   467789823    10238976   82  Linux swap / Solaris

Disk /dev/sdb: 3999.7 GB, 3999688294400 bytes
222 heads, 32 sectors/track, 1099646 cylinders, total 7811891200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe3ad23dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3905945599  1952971776   83  Linux

# sudo mkfs -t ext3 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122060800 inodes, 488242944 blocks
24412147 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14900 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done       

# sudo mount -a

# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       212G   53G  149G  27% /
devtmpfs         63G  4.0K   63G   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none             13G  1.1M   13G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             63G     0   63G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb1       1.8T  196M  1.7T   1% /home/nnovod/data

---

### Post by Nathaniel_Novod on 2014-05-03
Figured it out - MBR partitions (unix default?) can only handle up to 2Tb so I had to use parted (fdisk can't do GPT partitions) and create a GPT partition as follows...

# sudo parted /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: LSI MR9271-4i (scsi)
Disk /dev/sdb: 4000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext3

(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be
lost. Do you want to continue?
Yes/No? yes                                                               
(parted) print                                                            
Model: LSI MR9271-4i (scsi)
Disk /dev/sdb: 4000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart primary 0GB 4000GB                                        
(parted) print                                                            
Model: LSI MR9271-4i (scsi)
Disk /dev/sdb: 4000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  4000GB  4000GB  ext3         primary

(parted) quit                                                             
Information: You may need to update /etc/fstab.                           

# sudo mkfs -t ext3 /dev/sdb1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
244121600 inodes, 976485888 blocks
48824294 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
29800 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done       

# mount -a
# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       212G   53G  149G  27% /
devtmpfs         63G  4.0K   63G   1% /dev
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none             13G  1.1M   13G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             63G     0   63G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb1       3.6T  197M  3.4T   1% /home/nnovod/data

---

