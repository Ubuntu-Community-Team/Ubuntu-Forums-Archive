---
title: "No longer able to boot 12.04.3 using LVM - drops to busybox"
date: 2013-09-23
forum: General Help
---

### Post by hTCer6R on 2013-09-23
I am having trouble booting a 12.04.3 LTS server, which was running correctly until a recent power outage caused the box to fallover. Now when I try to boot it up, I get the following error message and the system drops to busybox and the initramfs prompt:[INDENT]
[FONT=courier new][38.045827] EXT3-fs (dm-1): error: unable to read superblock[/FONT]
[FONT=courier new][38.048857] EXT4-fs (dm-1): unable to read superblock[/FONT]
[FONT=courier new][38.052813] FAT-fs (dm-1): unable to read boot sector[/FONT]
[FONT=courier new]mount: mounting /dev/mapper/slartibartfast-root on /root failed: Invalid argument[/FONT]
[FONT=courier new]Begin: Running /scripts/local-bottom ... done.[/FONT]
[FONT=courier new]Begin: Running /scripts/init-bottom ... done.[/FONT]
[FONT=courier new]udevd[283]notify_add_watch(6, /dev/dm-3, 10) failed: Invalid argument[/FONT]
[FONT=courier new]udevd[284]: inotify_add_watch(6, /dev/dm-1, 10) failed: Invalid argument[/FONT]
[FONT=courier new]udevd[294]: inotify_add_watch(6, /dev/dm-4, 10) failed: Invalid argument[/FONT]
[FONT=courier new]mount: mounting /dev on /root/dev failed: No such file or directory[/FONT]
[FONT=courier new]mount: mounting /sys on /root/sys failed: No such file or directory[/FONT]
[FONT=courier new]mount: mounting /proc on /root/proc failed: No such file or directory[/FONT]
[FONT=courier new]Target filesystem doesn't have requested /sbin/init.[/FONT]
[FONT=courier new]No init found. Try passing init= bootarg.[/FONT][/INDENT]
[FONT=courier new]
[/FONT][INDENT][FONT=courier new]Busybox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)[/FONT]
[FONT=courier new]Enter 'help' for a list of built-in commands.[/FONT]

[FONT=courier new](initramfs) _
[/FONT][/INDENT]
[FONT=courier new]
[/FONT]Following a trawl through similar threads here, I have tried a combination of things - firstly running e2fsck against the filesystem and secondly, altering fstab to use the UUID of the device(s), rather than their mappings. Having tried both of these, I still get the same result.

I am able to mount the filesystem and chroot into that environment, so I dont think that the drive is corrupted beyond use, but I am stumped as to how to progress further!  Details of what I have tried, after booting into a LiveCD are pasted below:[INDENT][FONT=courier new]ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/slartibartfast/root
  LV Name                root
  VG Name                slartibartfast
  LV UUID                GEMCbT-pSfa-FrYJ-gLBe-3Mqu-376o-OQFVp6
  LV Write Access        read/write
  LV Creation host, time , 
  LV snapshot status     source of
                         root_snap [active]
  LV Status              available
  # open                 0
  LV Size                112.45 GiB
  Current LE             28786
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/slartibartfast/swap_1
  LV Name                swap_1
  VG Name                slartibartfast
  LV UUID                iNCrSI-yrgT-5wWn-xQ2X-9Uhn-eqdw-XaG07N
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                3.96 GiB
  Current LE             1015
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4

  --- Logical volume ---
  LV Path                /dev/slartibartfast/root_snap
  LV Name                root_snap
  VG Name                slartibartfast
  LV UUID                api7Mv-XaQm-ryKs-fev1-VnJV-fZvu-jIE0pC
  LV Write Access        read/write
  LV Creation host, time , 
  LV snapshot status     active destination for root
  LV Status              available
  # open                 0
  LV Size                112.45 GiB
  Current LE             28786
  COW-table size         100.00 GiB
  COW-table LE           25600
  Allocated to snapshot  17.51%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/slartibartfast-root

      117329 inodes used (1.59%, out of 7372800)
         134 non-contiguous files (0.1%)
          72 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 108815/51
     1462025 blocks used (4.96%, out of 29476864)
           0 bad blocks
           1 large file


       91248 regular files
       16428 directories
          55 character device files
          25 block device files
           0 fifos
          22 links
        9564 symbolic links (8375 fast symbolic links)
           0 sockets
------------
      117342 files
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/slartibartfast-root_snap
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1180875 (uid=102, gid=105, mode=0100600, size=0)
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1180874 (uid=102, gid=105, mode=0100600, size=0)
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1180873 (uid=102, gid=105, mode=0100600, size=0)
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1180872 (uid=102, gid=105, mode=0100600, size=0)
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1180871 (uid=102, gid=105, mode=0100600, size=0)
/dev/mapper/slartibartfast-root_snap: Clearing orphaned inode 1179652 (uid=0, gid=0, mode=0100600, size=0)

      104679 inodes used (1.42%, out of 7372800)
          87 non-contiguous files (0.1%)
          64 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 97497/78
    27492501 blocks used (93.27%, out of 29476864)
           0 bad blocks
          20 large files


       82000 regular files
       14385 directories
          55 character device files
          25 block device files
           0 fifos
          22 links
        8205 symbolic links (7016 fast symbolic links)
           0 sockets
------------
      104692 files

ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v /dev/mapper/slartibartfast-root
e2fsck 1.42.5 (29-Jul-2012)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
                                                                               
      117329 inodes used (1.59%, out of 7372800)
         134 non-contiguous files (0.1%)
          72 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 108815/51
     1462025 blocks used (4.96%, out of 29476864)
           0 bad blocks
           1 large file


       91248 regular files
       16428 directories
          55 character device files
          25 block device files
           0 fifos
          22 links
        9564 symbolic links (8375 fast symbolic links)
           0 sockets
------------
      117342 files

ubuntu@ubuntu:~$ sudo pvscan
  PV /dev/sda5   VG slartibartfast   lvm2 [232.64 GiB / 16.23 GiB free]
  Total: 1 [232.64 GiB] / in use: 1 [232.64 GiB] / in no VG: 0 [0   ]

ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "slartibartfast" using metadata type lvm2

ubuntu@ubuntu:~$ sudo lvscan
  ACTIVE   Original '/dev/slartibartfast/root' [112.45 GiB] inherit
  ACTIVE            '/dev/slartibartfast/swap_1' [3.96 GiB] inherit
  ACTIVE   Snapshot '/dev/slartibartfast/root_snap' [100.00 GiB] inherit[/FONT][/INDENT]

So after seeing that there appeared to be no errors on the drive itself, I thought I would trying mounting the filesystem using the UUID of the devices instead:[INDENT][FONT=courier new]ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="181f14dd-b959-442d-a30b-628bcae3c544" TYPE="ext2" 
/dev/sda5: UUID="NCFx2N-hHzA-6fae-BrYE-DY0K-0gTZ-gz1hTL" TYPE="LVM2_member" 
/dev/mapper/slartibartfast-root-real: UUID="ece5cd26-bb5d-40f7-8097-9e06bc5e95bb" TYPE="ext4" 
/dev/sdb: LABEL="media" UUID="7d9e4320-d7d1-411a-abbf-1f5fde240a12" TYPE="xfs" 
/dev/mapper/slartibartfast-root: UUID="ece5cd26-bb5d-40f7-8097-9e06bc5e95bb" TYPE="ext4" 
/dev/mapper/slartibartfast-root_snap-cow: TYPE="DM_snapshot_cow" 
/dev/mapper/slartibartfast-root_snap: UUID="ece5cd26-bb5d-40f7-8097-9e06bc5e95bb" TYPE="ext4" 
/dev/sdc1: UUID="298C-3F89" TYPE="vfat" 
/dev/mapper/slartibartfast-swap_1: UUID="5530337d-d4c6-44ae-9a99-55d91b98c59f" TYPE="swap" 
[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo mount /dev/mapper/slartibartfast-root /mnt[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo chroot /mnt[/FONT]
[FONT=courier new]ubuntu@ubuntu:~$ sudo nano /etc/fstab[/FONT][/INDENT]


****
ORIGINAL VERSION OF fstab
****[INDENT][FONT=courier new]# /etc/fstab: static file system information.[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# Use 'blkid' to print the universally unique identifier for a[/FONT]
[FONT=courier new]# device; this may be used with UUID= as a more robust way to name devices[/FONT]
[FONT=courier new]# that works even if disks are added and removed. See fstab(5).[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT]
[FONT=courier new]proc            /proc           proc    nodev,noexec,nosuid 0       0[/FONT]
[FONT=courier new]/dev/mapper/slartibartfast-root /               ext4    errors=remount-ro 0       1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# /boot was on /dev/sda1 during installation[/FONT]
[FONT=courier new]UUID=181f14dd-b959-442d-a30b-628bcae3c544 /boot           ext2    defaults        0       2[/FONT]
[FONT=courier new]/dev/mapper/slartibartfast-swap_1 none            swap    sw              0       0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# /dev/sdb      /media/raid5/   xfs     defaults,noatime,allocsize=512m,logbufs=8,sunit=128,swidth=256  0       2[/FONT]
[FONT=courier new]#/dev/sda       /media/raid5/   xfs     defaults,noatime,allocsize=512m,logbufs=8,sunit=128,swidth=256  0       2[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# RAID5 array, xfs format, mount to /media/raid5[/FONT]
[FONT=courier new]UUID=7d9e4320-d7d1-411a-abbf-1f5fde240a12       /media/raid5    xfs     defaults,noatime,nodiratime,allocsize=512m,logbufs=8,sunit=128,swidth=256   [/FONT][/INDENT]

****
REVISED VERSION OF fstab USING UUIDs 
****[INDENT][FONT=courier new]# /etc/fstab: static file system information.[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# Use 'blkid' to print the universally unique identifier for a[/FONT]
[FONT=courier new]# device; this may be used with UUID= as a more robust way to name devices[/FONT]
[FONT=courier new]# that works even if disks are added and removed. See fstab(5).[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT]
[FONT=courier new]proc            /proc           proc    nodev,noexec,nosuid 0       0[/FONT]
[FONT=courier new]#/dev/mapper/slartibartfast-root /               ext4    errors=remount-ro 0       1[/FONT]
[FONT=courier new]UUID=ece5cd26-bb5d-40f7-8097-9e06bc5e95bb /        ext4    errors=remount-ro 0       1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# /boot was on /dev/sda1 during installation[/FONT]
[FONT=courier new]UUID=181f14dd-b959-442d-a30b-628bcae3c544 /boot           ext2    defaults        0       2[/FONT]
[FONT=courier new]#/dev/mapper/slartibartfast-swap_1 none            swap    sw              0       0[/FONT]
[FONT=courier new]UUID=5530337d-d4c6-44ae-9a99-55d91b98c59f none     swap    sw              0       0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# /dev/sdb      /media/raid5/   xfs     defaults,noatime,allocsize=512m,logbufs=8,sunit=128,swidth=256  0       2[/FONT]
[FONT=courier new]#/dev/sda       /media/raid5/   xfs     defaults,noatime,allocsize=512m,logbufs=8,sunit=128,swidth=256  0       2[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# RAID5 array, xfs format, mount to /media/raid5[/FONT]
[FONT=courier new]UUID=7d9e4320-d7d1-411a-abbf-1f5fde240a12       /media/raid5    xfs     defaults,noatime,nodiratime,allocsize=512m,logbufs=8,sunit=128,swid$[/FONT][/INDENT]




Rebooting with the revised fstab gives the same result as the original problem and I am now stumped.

Any suggestions will be gratefully received!

---

### Post by hTCer6R on 2013-09-23
I've just noticed that the UUIDs reported by [COLOR=#000000][FONT=courier new]sudo blkid[/FONT][/COLOR] are different to those reported by [COLOR=#000000][FONT=courier new]sudo lvdisplay[/FONT][/COLOR].

I have been using the ones reported by [COLOR=#000000][FONT=courier new]sudo blkid[/FONT][/COLOR] rather than those from [COLOR=#000000][FONT=courier new]sudo lvdisplay[/FONT][/COLOR] in  [COLOR=#000000][FONT=courier new]/etc/fstab[/FONT][/COLOR], is that correct?

---

### Post by hTCer6R on 2013-09-24
I have posted the output of running boot-repair in the boot-repair thread: [http://ubuntuforums.org/showthread.php?t=1769482&p=12797511#post12797511](http://ubuntuforums.org/showthread.php?t=1769482&p=12797511#post12797511)

---

### Post by hTCer6R on 2013-09-24
I'm just wondering if one option would be to:
 
1) Boot into a LiveCD
2) Copy the existing LVM partition /dev/mapper/slartibartfast-root to USB drive
3) Do a fresh install of Ubuntu, setting the same partition sizes and upgrade to the latest builds
4) Recover the LVM partition from USB into the old location

Would that work? What about /dev, /sys and /proc which are (presumably) not backed up via the LVM snapshot?

---

### Post by steeldriver on 2013-09-24
sorry I'm pushed for time right now but since you're not getting much help so far, I just wanted to chime in - I have recovered a similar situation in which automated boot-repair failed to repair an LVM-based system and will try to post back and help later, iirc I had to perform the boot repair manually by chrooting in from a live CD, mounting the root LVM + /dev, /proc /sys, /run, and then purging and reinstalling grub

---

### Post by hTCer6R on 2013-09-24
> **steeldriver said:**
> sorry I'm pushed for time right now but since you're not getting much help so far, I just wanted to chime in - I have recovered a similar situation in which automated boot-repair failed to repair an LVM-based system and will try to post back and help later, iirc I had to perform the boot repair manually by chrooting in from a live CD, mounting the root LVM + /dev, /proc /sys, /run, and then purging and reinstalling grub

Thank you for taking the time to respond to my plea for help!

I have tried your suggestion - chrooted in from the live cd, mounted the root lvm, dev, proc, sys and run; then purged grub and linux-image image-generic (an additional step I found somewhere else); then reinstalled image-generic (which also reinstalled grub) and did an update-grub; exit the chroot; unmounted all partitions then rebooted.

Same issue as the original problem :-(

---

### Post by mcanada on 2013-09-25
I recently had the same issue as you, except with an Ubuntu 10.04.4 LTS server release. After spending some time on the problem I was able to resolve the issue. The key was being able to repair the logical volume.

Here is what I did:

1. Booted using the Ubuntu 12.04 Desktop Live CD. Once booted, opened the "Terminal" program
2. Type "*sudo apt-get install lvm2*" to install the lvm2 package
3. Type "*sudo pvscan*"
4. Type "*sudo vgscan*". This should give you a list of the volume groups as you have noted in your post.
5. Then I did this -> "*vgchange -a y groupname*". You will see the name of the root group from the command before. Replace "groupname" with the one for your system.
6. After that, you can access it via "/dev/mapper/groupname_root". To confirm, type "*sudo lvscan*" and look for the name of it under the /dev/mapper directory.
7. So at this point run the fsck command you tried already "*sudo e2fsck -C0 -p -f -v /dev/mapper/groupname_root*"
 
This resolved a couple of block issues with the volume group for me and was able to boot the system successfully afterwards.

---

