---
title: "Booting ubuntu from usb - does it matter from which partition ?"
date: 2013-09-15
forum: General Help
---

### Post by givz2 on 2013-09-15
Hi,  Sorry if I didn't put a correct prefix, this is my first post.   Anyhow: I created an installation of Xubuntu on my thumb drive in one partition formatted to ext4, and the rest of the drive I formatted as FAT32, thinking that doing so will enable windows to read it.  After I discovered that windows didn't comply with my wishes, I Googled it and realized that in order for the partition to be read by windows, it must be the first partition on the drive.  All hail Microsoft..  If I reverse the order of the partitions, would it still be possible for me to boot ubuntu from that device? or does Ubuntu's partition also has to be first in order to boot? If it matters. I'm currently not using a grub b/c most of the time I use the drive without booting from it.  Thanks!

---

### Post by sudodus on 2013-09-15
Welcome to the Ubuntu Forums :-)

I have made USB boot drives with a first FAT32 partition for exchange with Windows and a second partition for linux. This second partition could have any of FAT32, ext2, ext3 or ext4 file system. Because pendrives are sensitive to wear, you should not have journaling so ext2 is a good choice.

Do you intend to have make 'standard' live system, a persistent live system or an 'installed system' on the USB pendrive?

---

### Post by ajgreeny on 2013-09-15
It does not matter which partition your ubuntu OS is on; it can boot from any, so you can reinstall, this time with the fat32 partition at the front of the drive and your ubuntu OS in the second partition.  Are you sure this is a full installation and not just a live system that you're using?

If you are not using grub how are you managing to boot ubuntu at all? It must have a bootloader system of some kind, so I am a little confused.

---

### Post by CeejRab on 2013-09-15
Hello Givs2, 

First, I highly encourage you not to use EXT 3/4 file systems on an SSD drive, the journaling harms the drive over time and is can corrupt blocks in the storage. 

Second, you don't need to format it to anything but FAT-32 to have a live CD on it... Is it a live cd or full install of xubuntu? If you only need a live CD, don't bother with partitioning, just use PendriveLinux's "universal USB installer" to set it up. 

Thirdly, your device normally boots from the main device table, not from specific partitions, so as long as you have a syslinux or grub boot loader in the usb's mbr it should be recognized and boot up nicely. 

Try using YUMI Multiboot if you want more than one distro on your USB drive. Also, the drive will be easily viewed and used on any OS if its FAT-32.

All the best,

-Christian

---

### Post by givz2 on 2013-09-15
Wow, thanks for the replies!  Actually, I started with a live usb installation using "YUMI" installer, but somehow managed to mess up  the  win7 boot and had to re-install it.   That's another reason I'm not using grub - I don't want to mess it up again.  In the meanwhile, when I want to boot Ubuntu I change the order of boot in the bios. Clearly not the most elegant way..  I had a lot of mess trying to put  a working ubuntu on my drive,  so I'm not actually 100% sure what I'm running now is a full installation. But I'm quite sure that I had to, because of persistence issues, and now the information is kept after reboot. How can I tell for sure..?  Good to know about the EXT / flash drive issue. I get the notion that for a full installation I can't use FAT32, so I'll probably go for the EXT2 advice.  I really appreciate the help guys!

---

### Post by ajgreeny on 2013-09-15
Two simple ways to tell.
[LIST=1]
[*]If there is an "Install Ubuntu" icon on the desktop or in the launcher bar you have a live system, not a full installation.
[*]Run the command sudo fdisk -l in terminal (Ctrl+Alt+T) and report the output back here.  We can soon tell you if it's a live system or installed system from that.
[/LIST]
If you have a live system but do want a full installation on the USB, it can easily be done, but bear in mind the comments above about non journalling filesystem, ext2 and no swap.

Choose **Something Else **at disk preparation/partitioning stage and you will get the option of where to install grub bootloader.  If you make sure it goes on to the root of your usb drive, the windows bootloader will remain untouched on your hard drive.

Now set the machine boot priority to the usb and if it is inserted when you boot up the computer you will see the grub menu and be able to boot either OS.  If the usb is not inserted windows will boot normally, as grub will be totally missing (it's on the usb) and you will not see any difference to the system from how it was before ubuntu was installed.

---

### Post by sudodus on 2013-09-15
If you have an 'installed system' on the USB drive, you should add the mount option noatime in /etc/fstab to reduce writing operations.

You can get help to know what kind of system you have if you run the command

```
df
```

(or for more details)

```
 cat /etc/mtab
```

and post the output within code tags in a reply. Write like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

or mark the text and click the # icon at the top of the editing window.

---

### Post by givz2 on 2013-09-15
Checking for the installation icon was also my intuition, it seems that it is an installation. sudodus - I didn't get the part about /etc/fstab . Tried to access it from terminal by putting the address and got "Permission Denied". With sudo I got "command not found".  ajgreeny - I'll try the "Something Else" option for the grub, is it possible to implement this without running over the currently installed ubuntu?  Two outputs you both mentioned: 1. sudo fdisk -l  : ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x02900290     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT /dev/sda2       102398310   312576704   105089197+   f  W95 Ext'd (LBA) /dev/sda5       102398373   312576704   105089166    7  HPFS/NTFS/exFAT  Disk /dev/sdb: 16.0 GB, 16013852672 bytes 64 heads, 32 sectors/track, 15272 cylinders, total 31277056 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0xfafbfafb     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *        8064    12703376     6347656+  83  Linux /dev/sdb2        12703744    31277055     9286656    b  W95 FAT32  
```  2.  cat /etc/mtab : ```
  /dev/sdb1 / ext4 rw,errors=remount-ro 0 0 proc /proc proc rw,noexec,nosuid,nodev 0 0 sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0 none /sys/fs/fuse/connections fusectl rw 0 0 none /sys/kernel/debug debugfs rw 0 0 none /sys/kernel/security securityfs rw 0 0 udev /dev devtmpfs rw,mode=0755 0 0 devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0 none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0 none /run/shm tmpfs rw,nosuid,nodev 0 0 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0 /home/z/.Private /home/z ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=c7ae5d125837bcf5,ecryptfs_fnek_sig=ecb92535df961298 0 0 gvfs-fuse-daemon /home/z/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=z 0 0 /dev/sda5 /media/\040\040\040  fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0 /dev/sdb2 /media/87A6-64CC vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0 
```

---

### Post by givz2 on 2013-09-15
btw, why do my posts come out as a one long paragraph even though I put a row between two sentences?

---

### Post by sudodus on 2013-09-15
> **givz2 said:**
> btw, why do my posts come out as a one long paragraph even though I put a row between two sentences?

That is a good question ;-) I think because of the way you copied and pasted it and let it be pre-processed before putting the code tags. This forum editor is a little tricky, but you will learn ...

I put line-feeds at suitable places to make it readable

sudo fdisk -lu:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02900290

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       102398310   312576704   105089197+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   312576704   105089166    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
64 heads, 32 sectors/track, 15272 cylinders, total 31277056
sectors Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfafbfafb
     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    12703376     6347656+  83  Linux
/dev/sdb2        12703744    31277055     9286656    b  W95 FAT32
```

cat /etc/mtab:

```

/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/z/.Private /home/z ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=c7ae5d125837bcf5,ecryptfs_fnek_sig=ecb92535df961298 0 0
gvfs-fuse-daemon /home/z/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=z 0 0 /dev/sda5 /media/\040\040\040  fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb2 /media/87A6-64CC vfat rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0
```

mtab tells me that it is an installed system, because the root file system is a partition on a drive (sdb, the pendrive), not ramdrive.

---

