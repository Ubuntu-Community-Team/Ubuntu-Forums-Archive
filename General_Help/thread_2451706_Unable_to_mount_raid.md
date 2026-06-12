---
title: "Unable to mount raid"
date: 2020-10-09
forum: General Help
---

### Post by asb3 on 2020-10-09
I'm running ubuntu 20.04.
I recently set up pair of a WD 4T usb hard drives as a raid1.  I can no longer mount the raid.
After working fine for two weeks, an hour ago I started to be I/O errors when I tried to read files.  The lights on the front of the drives that come on when the drive is powered up and connected went off.  The drives are plugged in to a power strip on the floor under my desk, and I think I accidentally stepped on the on/off switch, powering down the drives. 
The strange thing is that I was able to list the directories, even when the drives were powered down!
I powered up the drives; no improvement.
I powered off the computer, checked the usb connections, and rebooted.  The machine took a long time to reboot.  When it finally booted successfully, the raid was not mounted.
I tried to mount the drive and got an error:
>mount /mnt/data
mount: /mnt/data: special device /dev/md127p1 does not exist.

Here's the result of lsblk:
>lsblk
NAME                MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                 7:0    0   162M  1 loop  /snap/chromium/1320
loop1                 7:1    0   240M  1 loop  /snap/chromium/1328
loop2                 7:2    0 255.6M  1 loop  /snap/gnome-3-34-1804/36
loop3                 7:3    0  97.1M  1 loop  /snap/core/9993
loop4                 7:4    0  96.6M  1 loop  /snap/core/9804
loop5                 7:5    0 260.7M  1 loop  /snap/kde-frameworks-5-core18/32
loop6                 7:6    0    55M  1 loop  /snap/core18/1880
loop7                 7:7    0  55.3M  1 loop  /snap/core18/1885
loop8                 7:8    0  62.1M  1 loop  /snap/gtk-common-themes/1506
loop9                 7:9    0  30.3M  1 loop  /snap/snapd/9279
loop10                7:10   0  29.9M  1 loop  /snap/snapd/8790
loop11                7:11   0 217.9M  1 loop  /snap/gnome-3-34-1804/60
loop12                7:12   0 177.8M  1 loop  /snap/digikam/12
sda                   8:0    0 223.6G  0 disk  
&#9500;&#9472;sda1                8:1    0   243M  0 part  
&#9500;&#9472;sda2                8:2    0     1K  0 part  
&#9492;&#9472;sda5                8:5    0 223.3G  0 part  
  &#9500;&#9472;ubuntu-root     253:2    0 191.6G  0 lvm   /mnt/hd1
  &#9492;&#9472;ubuntu-swap_1   253:3    0  31.7G  0 lvm   [SWAP]
sdb                   8:16   0  59.6G  0 disk  
&#9500;&#9472;sdb1                8:17   0   512M  0 part  /boot/efi
&#9500;&#9472;sdb2                8:18   0     1K  0 part  
&#9492;&#9472;sdb5                8:21   0  59.1G  0 part  
  &#9500;&#9472;vgubuntu-root   253:0    0  58.2G  0 lvm   /
  &#9492;&#9472;vgubuntu-swap_1 253:1    0   980M  0 lvm   [SWAP]
sdc                   8:32   0   1.8T  0 disk  
&#9492;&#9472;sdc1                8:33   0   1.8T  0 part  
  &#9492;&#9472;md0               9:0    0   1.8T  0 raid1 /mnt/hd2
sdd                   8:48   0   1.8T  0 disk  
&#9492;&#9472;sdd1                8:49   0   1.8T  0 part  
  &#9492;&#9472;md0               9:0    0   1.8T  0 raid1 /mnt/hd2
sde                   8:64   0   3.7T  0 disk  
&#9492;&#9472;sde1                8:65   0   3.7T  0 part  
  &#9492;&#9472;md1               9:1    0   3.7T  0 raid1 
    &#9492;&#9472;md1p1         259:1    0   3.7T  0 part  
sdf                   8:80   0   3.7T  0 disk  
&#9492;&#9472;sdf1                8:81   0   3.7T  0 part  
  &#9492;&#9472;md1               9:1    0   3.7T  0 raid1 
    &#9492;&#9472;md1p1         259:1    0   3.7T  0 part  
sr0                  11:0    1  1024M  0 rom   

Here's /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=CBFC-3D4C  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/mapper/vgubuntu-swap_1 none            swap    sw              0       0
UUID=7a420995-9611-46f9-8e1f-d177783b5794 /mnt/hd1 ext4 defaults 0 2
/dev/md127p1     /mnt/data     ext4     defaults     0 0
/dev/md0     /mnt/hd2     ext4     defaults     0 0

Here's the information on the drives displayed by gparted, plus the same info for the internal drives sdc and sdd that are mounted also mounted as a raid1:
Partition       Name         File System    Mount Point  Label      Size         Used    Unused    Flags
/dev/sdc1                       linux-raid        /dev/md0      cavu:0    1.82 TiB    --         --             
/dev/sdd1                       linux-raid        /dev/md0      cavu:0    1.82TiB     --         --             
/dev/sde1     Elements    linux-raid        /dev/md1      cavu:1    3.64 TiB    --         --              msftdata
/dev/sdf1      Elements    linux-raid        /dev/md1      cavu:1    3.64 TiB     --         --             msftdata

Is the msftdata flag the problem? Would it help to remove it?  
Help!

---

### Post by helen314 on 2020-10-09
I have had some luck using mdadm... 

never mind - just noticed the thread is SOLVED

---

