---
title: "ubuntu failed to mount errors"
date: 2016-09-02
forum: General Help
---

### Post by squarethumps on 2016-09-02
Long story short :   Too much dust in the machine caused some overheating and an unsolicitied hard shutdown.   Since then ubuntu will not boot.   Dual boot system ( Windows and Ubuntu ).  Grub still boots.  Windows still boots.   Ubuntu will not a la these types of errors : 

[https://ubuntuforums.org/showthread.php?t=1244466](https://ubuntuforums.org/showthread.php?t=1244466)

I have booted into the LiveCD.  Here is my output.    If the installation can be repaired, that would be ideal.  If not, I would just like to get the data off the disk. 

```

root@ubuntu:~# 
root@ubuntu:~# fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   341130705   170461929    7  HPFS/NTFS/exFAT
/dev/sda3       341131262  1250263039   454565889    5  Extended
/dev/sda5       341131264  1241876479   450372608   83  Linux
/dev/sda6      1241878528  1250263039     4192256   82  Linux swap / Solaris
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="8CB499ADB49999F2" TYPE="ntfs" 
/dev/sda2: UUID="563CAF7D3CAF56B1" TYPE="ntfs" 
/dev/sda5: UUID="2aa729d4-5b63-4162-98d3-b7a8b500cf0a" TYPE="ext4" 
/dev/sda6: UUID="8bd08c79-f119-421b-8425-968e11c68af5" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# mkdir /mnt/ubuntu_disk
root@ubuntu:~# mount /dev/sda5 /mnt/ubuntu_disk/
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# dmesg | tail
[ 1615.108691]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1615.108704]         2f 19 4a 50 
[ 1615.108710] sd 2:0:0:0: [sda]  
[ 1615.108713] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1615.108716] sd 2:0:0:0: [sda] CDB: 
[ 1615.108718] Read(10): 28 00 2f 19 4a 48 00 00 f8 00
[ 1615.108729] end_request: I/O error, dev sda, sector 790186576
[ 1615.108758] ata3: EH complete
[ 1615.108980] JBD2: recovery failed
[ 1615.108991] EXT4-fs (sda5): error loading journal
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 

```



I'm not sure what the next steps are here ? 

Any help is MOST appreciated.

---

### Post by squarethumps on 2016-09-02
Oh, YA !!!!!! 


```

root@ubuntu:~# fsck /dev/sda5 
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda5: recovering journal
Error reading block 56131912 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Clearing orphaned inode 27395272 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 27394934 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 19267590 (uid=112, gid=118, mode=0100600, size=65536)
Clearing orphaned inode 27394755 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 27394754 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 27394720 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 27394752 (uid=112, gid=118, mode=0100664, size=2363)
Clearing orphaned inode 27394748 (uid=112, gid=118, mode=0100664, size=2363)
Setting free inodes count to 27158406 (was 27158424)
Setting free blocks count to 96528488 (was 96528548)
/dev/sda5: clean, 997498/28155904 files, 16064664/112593152 blocks
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# mount /dev/sda5 /mnt/ubuntu_disk/
root@ubuntu:~# 


```

---

