---
title: "Help with LVM removal/ Getting an New Partition to Mount"
date: 2014-10-20
forum: General Help
---

### Post by locustmage420 on 2014-10-20
So heres the deal. Ive been running windows for a while and now im in Linux System Administration in college and I needed a full Linux install to use to do my Lab reports outside of class. So I installed Ubuntu again, and when I did I realized I had a hidden 250 gbs or so of space taken up by a previous fedora install in the form of an LVM. Without knowing exactly what I was doing, I used the disks utility to change the partition type to Linux (from LVM) then format the drive. I am trying to mount the hard drive to the location /home/jason/Public/UbuntuMusic. I have formatted it twice and still upon booting it tells me that the hard disk for /home/jason/Public/UbuntuMusic is not ready. When I try to mount the partition using disks utility it brings up this error message

Error mounting system-managed device /dev/sdb2: Command-line `mount "/home/jason/Public/UbuntuMusic"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)



now after researching it a bit. It seems that I should have deactivated the LVM first with  sudo lvremove  however i cant do that now... Any help would be appreciated. Below is the /etc/fstab

 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=f4b9952f-32fb-44fc-bc02-03cd5a47c013 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a39bdc45-bd80-4037-ba22-f2e7866df27d /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a4c0f226-17a8-45b0-a38a-fba2a7206dab none            swap    sw              0       0
/dev/sdb1 /home/jason/Public/Movies auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Movies 0 0
/dev/sda1 /home/jason/Public/Music auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Music 0 0
/dev/sdc2 /home/jason/Public/Windows auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Windows 0 0
/dev/sdb2 /home/jason/Public/UbuntuMusic auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=UbuntuMusic 0 0

---

### Post by nerdtron on 2014-10-20
Is this server install of you used a GUI to format the /dev/sdb2 partition? What commands did you use to format it?
Please provide also the output of 
```
 sudo fdisk -l
sudo parted -l 
```

*note that it a lower case L*

---

### Post by oldfred on 2014-10-20
Post this, just want to make sure of format.
sudo parted -l

Better to always mount with UUIDs, but that is a separate issue. Device numbers can change. My system has 4 drives and if I plug in a flash drive, it is sde, but if I reboot the flash drive becomes sdb and every other drive is one letter more. I think I skipped a SATA port on motherboard.

If not mounted, you can run this from your install. But only ever run on umounted partitions and usually then you have to use live installer to run it on  your mounted install.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by locustmage420 on 2014-10-20
this is a ubuntu 14.04 desktop install
i used the gui tool

Sorry had to edit the post. I posted the fdisk twice. The first time I ran it, I seen that. That was me trying to switch the type back to LVM to try to run lvremove. But what's there now is the proper output of fdisk

jason@jason-Studio-XPS-435MT:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96c8bf2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1748721663   874359808    7  HPFS/NTFS/exFAT
/dev/sda2      1748723710  1953523711   102400001    5  Extended
/dev/sda5      1748723712  1760440319     5858304   82  Linux swap / Solaris
/dev/sda6      1760442368  1815128063    27342848   83  Linux
/dev/sda7      1815130112  1953523711    69196800   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77f0d358

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb105

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953525167   976761560    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93d37b8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1408983039   704490496    7  HPFS/NTFS/exFAT
/dev/sdb2      1408985088  1953525167   272270040   83  Linux


sudo parted -l

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  895GB   895GB   primary   ntfs            boot
 2      895GB   1000GB  105GB   extended
 5      895GB   901GB   5999MB  logical   linux-swap(v1)
 6      901GB   929GB   28.0GB  logical   ext4
 7      929GB   1000GB  70.9GB  logical   ext4


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  721GB   721GB  primary  ntfs
 2      721GB   1000GB  279GB  primary  ext4


Model: ATA ST31000528AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   1000GB  1000GB  primary  ntfs


Model: ATA ST31000528AS (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs

---

### Post by oldfred on 2014-10-20
Your fdisk shows this:
/dev/sdb2      1408985088  1953525167   272270040   8e  Linux LVM

But parted shows this:
/dev/sdb2      1408985088  1953525167   272270040   83  Linux

But I thought this was from the partition table in the MBR of sdb so the 8e and 83 should be just 83.
Not sure where fdisk is then seeing the 8e entry?

---

### Post by locustmage420 on 2014-10-20
Output of:

    sudo e2fsck -C0 -p -f -v /dev/sdb2



      11 inodes used (0.00%, out of 17022976)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
     1116241 blocks used (1.64%, out of 68067510)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------

---

### Post by oldfred on 2014-10-20
If you go into Disks or Disk utility what does it say about sdb2?

I know with Disk Utility you could manually edit the partition type. If no data to worry about i might see if I could reset to 83 in Disks.

---

### Post by locustmage420 on 2014-10-21
So as I stated in my edit, I was using the the disk utility to try to change it back to lvm to run lvremove. What's there now is what it was. However I altered /etc/fstab to reflect UUIDs instead of /dev/* identifiers. The partitions all mounted on boot except the one in question. After switching to a different mount point, (I chose /home/jason/Public/Ubuntu  rather than ./UbuntuMusic) it mounts but still wont mount at boot. The check box for that is checked in disk utility.

---

### Post by buzzingrobot on 2014-10-21
The way I've found to deal with LVM setups is not to try to repurpose them, etc., but just to delete them entirely with parted. (Or gparted.) If the partitions are mounted, parted will complain, but offers options to plow on through.  On reboot -- you need to reboot so the kernel picks up the changes -- a new partition table can be added, either within an installer, or not.

Re: LVM -- Is there an uptodate, reliable explanation of how to do a multi-disk LVM install of Ubuntu? Fedora's installer handles this smoothly, but Ubuntu's installer seems only to deal with one disk, which rather seems to defeat the value of LVM. (OK, off to start a new thread.;))

---

### Post by oldfred on 2014-10-21
If dual booting there is little reason to use LVM. The advantage of LVM is when it controls entire drive. Those dual booting with Fedora are suggested to not use LVM and in its advanced install choose just ext4.

I think Herman discusses LVM multiple booting here:
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by buzzingrobot on 2014-10-21
> **oldfred said:**
> If dual booting there is little reason to use LVM. The advantage of LVM is when it controls entire drive. Those dual booting with Fedora are suggested to not use LVM and in its advanced install choose just ext4.

I think Herman discusses LVM multiple booting here:
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Not dual booting. In Fedora, opting to allow the installer (Anaconda) to setup the partitions automatically, you'll get an LVM install using all selected drives, using XFS. I zap the existing partitions before booting into the installer, so it uses all of the two drives I select. That's what I want to duplicate on Ubuntu.

Thanks for the link; I'll check it out.

---

