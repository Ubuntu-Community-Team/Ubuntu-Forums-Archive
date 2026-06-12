---
title: "Help needed moving /usr to a new partition"
date: 2012-12-24
forum: General Help
---

### Post by FrankJC on 2012-12-24
After my / directory kicked out an error message that I was running out of space on my root partition, I decided to move my /usr directory to its own partition.  I haven't had much success even after reading what I could find on the internet.  After doing this and trying to reboot, the system either hangs on the ubuntu page with the dots or simply goes black and I have to power down.  If someone has any ideas about what I am doing wrong, I would appreciate any hints or help.

What I have tried so far is:
Booting up ubuntu from a cd (live), then:

I mounted my unused partition (sda7) .... see below to see what's on it after I copied the contents of my /usr

cd /
sudo mkdir /mnt/newusr
sudo mount /dev/sda7 /mnt/newusr

Then I mounted my / directory:
sudo mkdir /mnt/mydisk
sudo mount /dev/sda11 /mnt/mydisk

Moved to my usr directory:
cd /mnt/mydisk/usr

Copied the files to sda7 with:
sudo rsync  -aXS  --exclude='/*/.gvfs'  /usr/.  /newusr/.
(I don't quite know why the --exclude part is there, but I don't think it was necessary)

I then edited my fstab file to include the line:
UUID=d46e4252-9906-4fc9-a735-abec92836afe       /usr    ext3    defaults        0       2

I renamed my mnt/mydisk/usr to oldusr
sudo mv /mnt/mydisk/usr /mnt/mydisk/newusr

After mounting /usr on /dev/sda7... I have the following two directories:
lost+found and usr
Under usr are: bin, games, include, lib, local, sbin, share, src

Output from ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 4CBC7A96BC7A79F2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 46BD-55C0 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 4C97FE372E776669 -> ../../sda5
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 16CCA7BB4DBD1724 -> ../../sda6
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 d46e4252-9906-4fc9-a735-abec92836afe -> ../../sda7
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 505db12a-889d-4b82-b424-335a4c3725cf -> ../../sda8
lrwxrwxrwx 1 root root 10 2012-12-24 08:34 c6f07bdb-b0c8-4dd7-bc20-2bf68b5e359c -> ../../sda9
lrwxrwxrwx 1 root root 11 2012-12-24 08:34 56433992-aca3-403e-a9da-1a81bb818d62 -> ../../sda10
lrwxrwxrwx 1 root root 11 2012-12-24 08:34 b3d9919d-5c29-4212-9d8a-947a36ae8676 -> ../../sda11
lrwxrwxrwx 1 root root 11 2012-12-24 08:34 5151d5a8-abe8-454e-a835-22c209b4f76f -> ../../sda12



Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43225087    21612512+   7  HPFS/NTFS/exFAT
/dev/sda2        43225088    61796351     9285632    c  W95 FAT32 (LBA)
/dev/sda3        69476350   488396799   209460225    5  Extended
/dev/sda5        69476352   173744127    52133888    7  HPFS/NTFS/exFAT
/dev/sda6       173746176   300193791    63223808    7  HPFS/NTFS/exFAT
/dev/sda7       319821824   341897215    11037696   83  Linux
/dev/sda8       341899264   408848383    33474560   83  Linux
/dev/sda9       408850432   482107391    36628480   83  Linux
/dev/sda10      482109440   488396799     3143680   82  Linux swap / Solaris
/dev/sda11      300195840   313518079     6661120   83  Linux
/dev/sda12      313520128   319805439     3142656   82  Linux swap / Solaris

Here are the contents of my fstab file:


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=b3d9919d-5c29-4212-9d8a-947a36ae8676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=5151d5a8-abe8-454e-a835-22c209b4f76f none            swap    sw              0       0
UUID=505db12a-889d-4b82-b424-335a4c3725cf /home         ext3    nodev,nosuid    0       2

---

