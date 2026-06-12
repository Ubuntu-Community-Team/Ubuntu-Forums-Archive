---
title: "How to show a SSD HD on Other Location"
date: 2022-01-05
forum: General Help
---

### Post by satimis on 2022-01-05
Hi all,

On this computer I have other HDs;
a 1TB Nvme PCIe 3.0x4 SSD HD on this PC, running Ubuntu 20.04
a 4TB WD HD for data storage without OS running
Booting controlled via BIOS

On
-> Files -> Other Locations
It only shows the 4TB WD HD (pls refers to attached screenshot)
1TB SSD HD missing

Please advise how to show the 1TB SSD HD

Thanks

Regards

---

### Post by Bashing-om on 2022-01-06
Hey satimis -

What shows terminal command:
```

sudo parted -l

```

If not seen here one will have to look at bios and hardwire connections.

-my bit to try and help-

---

### Post by satimis on 2022-01-06
> **Bashing-om said:**
> Hey satimis -

What shows terminal command:
```

sudo parted -l

```

If not seen here one will have to look at bios and hardwire connections.

Thanks for your advice.

On Terminal ran;
$ sudo parted -l > parted.txt

The output file is attached here

Regards

Edit
===
It is there```

Model: INTEL SSDPEKNW010T8 (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
```

---

### Post by Bashing-om on 2022-01-06
welp --

Disk /dev/nvme0n1: 1024GB >> 2   538MB   1024GB  1024GB    lvm

The drive is there and set up for LVM/

I have no experience here so the rest is up to others.

-A know it all I am not-

---

### Post by Dennis N on 2022-01-06
> Please advise how to show the 1TB SSD HD
Some devices in this "Other Locations" window are filtered out. Devices mounted through an entry in /etc/fstab will not appear here, but will appear in parted output. Access such devices through their mount point. I suggest you make bookmarks for quick access from the file manager side pane.

---

### Post by satimis on 2022-01-06
> **Dennis N said:**
> Some devices in this "Other Locations" window are filtered out. Devices mounted through an entry in /etc/fstab will not appear here, but will appear in parted output. Access such devices through their mount point. I suggest you make bookmarks for quick access from the file manager side pane.
Here is /etc/fstab

$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=f60e0b05-1944-402f-8029-81a9013711bc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7735-7864  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw  

```

Regards

---

### Post by Dennis N on 2022-01-06
It would help to post the output of:
```
lsblk -o name,fstype,mountpoint
```
to expose more details of the LVM structure on the NVMe device.

---

### Post by satimis on 2022-01-06
> **Dennis N said:**
> It would help to post the output of:
```
lsblk -o name,fstype,mountpoint
```
to expose more details of the LVM structure on the NVMe device.

$ lsblk -o name,fstype,mountpoint```

NAME        FSTYPE      MOUNTPOINT
loop0       squashfs    /snap/bare/5
loop1       squashfs    /snap/gnome-3-34-1804/77
loop2       squashfs    /snap/gtk-common-themes/1515
loop3       squashfs    /snap/gnome-3-34-1804/72
loop4       squashfs    /snap/core18/2128
loop5       squashfs    /snap/core20/1270
loop6       squashfs    /snap/snap-store/558
loop7       squashfs    /snap/snapd/12704
loop8       squashfs    /snap/core18/2253
loop9       squashfs    /snap/gtk-common-themes/1519
loop10      squashfs    /snap/gnome-3-38-2004/87
loop11      squashfs    /snap/snap-store/547
loop12      squashfs    /snap/snapd/14295
sda                     
&#9492;&#9472;sda1      ext4        
sdb                     
&#9500;&#9472;sdb1      vfat        /boot/efi
&#9492;&#9472;sdb2      ext4        /
nvme0n1                 
&#9500;&#9472;nvme0n1p1 vfat        
&#9492;&#9472;nvme0n1p2 LVM2_member 

```

$ ls -l /dev/disk/by-uuid```

total 0
lrwxrwxrwx 1 root root 15 Jan  7 11:28 0E3A-4ABA -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 10 Jan  7 11:28 7735-7864 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jan  7 11:28 786a6a67-06f5-428f-a24d-fe75cd0b08d5 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan  7 11:28 f60e0b05-1944-402f-8029-81a9013711bc -> ../../sdb2

```

Regards

---

### Post by Dennis N on 2022-01-07
On the NVME drive, the LVM2 member is not directly mountable, so won't display in Files. You will need to make a volume group (VG) containing p2, and then a logical volume (LV) in that volume group which can then be formatted ext4. After that, the file manager will show the ext4 file system that was created in the "Other Locations". 

To do these tasks, you need to understand LVM concepts and LVM commands, which requires some study on your part if you don't already know how. 

Here is the same setup on this computer, but with two logical volumes added, each formatted ext4 and with an OS installed on it:
```
nvme0n1                           
&#9500;&#9472;nvme0n1p1                          vfat        
&#9492;&#9472;nvme0n1p2                          LVM2_member 
  &#9500;&#9472;wdsn500-manjaro--nvme            ext4        
  &#9492;&#9472;wdsn500-ubuntu_1904              ext4        

```
There are many tutorials and articles about LVM on the web, but here are two I used to learn about LVM several years ago:
[Ubuntu LVM Guide]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html")
It's a bit old, but the commands haven't changed. Ignore any references to the GUI tool mentioned, as it's no longer available and you don't need it.
Also read and study this article:
[LVM Demystified]("http://www.linuxjournal.com/content/lvm-demystified")

---

### Post by satimis on 2022-01-07
> **Dennis N said:**
> On the NVME drive, the LVM2 member is not directly mountable, so won't display in Files. You will need to make a volume group (VG) containing p2, and then a logical volume (LV) in that volume group which can then be formatted ext4. After that, the file manager will show the ext4 file system that was created in the "Other Locations". 

To do these tasks, you need to understand LVM concepts and LVM commands, which requires some study on your part if you don't already know how. 

Here is the same setup on this computer, but with two logical volumes added, each formatted ext4 and with an OS installed on it:
```
nvme0n1                           
&#9500;&#9472;nvme0n1p1                          vfat        
&#9492;&#9472;nvme0n1p2                          LVM2_member 
  &#9500;&#9472;wdsn500-manjaro--nvme            ext4        
  &#9492;&#9472;wdsn500-ubuntu_1904              ext4        

```
There are many tutorials and articles about LVM on the web, but here are two I used to learn about LVM several years ago:
[Ubuntu LVM Guide]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html")
It's a bit old, but the commands haven't changed. Ignore any references to the GUI tool mentioned, as it's no longer available and you don't need it.
Also read and study this article:
[LVM Demystified]("http://www.linuxjournal.com/content/lvm-demystified")

Thanks for your advice.

This is a newly added 500G SATA 6G/s SSD HD.  I purchased this SSD for testing KVM/QEMU and Video Editing software, in particular Shotcut, running on bare-metal HD, in combination.

1st I selected Linuxmint 11.2 as host of KVM/QEMU.  KVM/QEMU works without problem but unfortunately Shotcut unable to run on Linuxmint 11.2.  On File Manager of Linuxmint 11.2, the 1TB NVMe PCIe SSD can be displayed.  Files can be shared btw the 1TB SSD and 500G SSD. 

Then I wiped out Linuxmint 11.2 and installed Debian 20.2.  But I couldn't make my Dell 32" 4K display to work,

Again I wiped out Debien 20.2 and installed Ubuntu 20.04, coming to the present situation.  Shotcut and Avidemux Video Editors works on the bare-metal SSD.  I haven't tested KVM/QEMU yet.

I have a spare PC with following HD config:
HD-1 2TB SSD running Ubuntu 20.04
HD-2 2TB WD HD for data storage
HD-3 2TB WD HD for data storage
HD-4 500G SSD running Windows 10
HD-5 250G SSD running Ubuntu 20.04

It has the same situation.  HD-1 is unable to be mounted automatically on HD-5 after starting Ubuntu 20.04,  Files sharing btw HD-1 and HD-5 is unable to work.

On HD-5 of the spare PC Terminal
$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2fc7a0c1-f447-46b1-ba7c-ebc7a7ec9bf2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5DFD-253C  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

$ lsblk -o name,fstype,mountpoint
(please refer to attached mountpoint.txt file)

If the problem is unable to solve I'll leave it, at least I can test Video Editing softwares here, running on bare-metal HD

Lot of thanks for your advice.

Regards

---

### Post by Dennis N on 2022-01-07
Did you intentionally choose LVM when you created p2 on the NVMe drive? Otherwise, you could just format p2 again to ext4 if you don't want to get into LVM.  But, I can tell you from experience that it is worthwhile to learn and use LVM. I think the advantages are explained in the linked articles. I now use LVM only and haven't look back.

As for sharing files between Linux systems, I use a separate data partition that can be mounted and used by any of them. 

Looking at your attachment, sdc has the same problem as the NVMe drive just discussed - no mountable Linux filesystem. You have a number of NTFS formatted partitions on sda and sdb. I haven't used NTFS at all in connection with Linux, so can't comment on using that file system or sharing it.

---

### Post by satimis on 2022-01-07
> **Dennis N said:**
> Did you intentionally choose LVM when you created p2 on the NVMe drive? Otherwise, you could just format p2 again to ext4 if you don't want to get into LVM.  But, I can tell you from experience that it is worthwhile to learn and use LVM. I think the advantages are explained in the linked articles. I now use LVM only and haven't look back.
I suppose p2 mentioned by you is my daily working PC, on which I just added a 500G SATA3 6G/s SSD.  This PC has been running at least 4 years including Ubuntu 20.04 installed on the 1TB NVMe PCI3 Gen 3.0 SSD.  LVM was originally installed.  I have been running LVM quite sometimes.

> 
As for sharing files between Linux systems, I use a separate data partition that can be mounted and used by any of them. 
I can use the 4TB WD HD for sharing data.  Of course it is not so convenient as sharing data direct on 2 OSs.  What I can't resolve is the 1TB SSD can connect the 500G SSD after starting Ubuntu 20.04, sharing data between them but not the other way round, 500G SSD unable to connect 1TB SSD, after starting Ubuntu 20.04.

I'll leave the problem unsolved because it is only a test, for checking the hardware forward capability of KVM/QEMU compared with VirtualBox which is running on the 1TB NVMe SSD.  I'm prepared to build a new AMD Ryzen 7 PC when I have spare time.

Another funny thing to me is Shotcut unable to run on bare-metal Linuxmint 11.2 but able to run on Linuxmint 11.2 VM of VirtualBox

Anyway lot of thanks for your help.

Best Regards

---

### Post by TheFu on 2022-01-07
I didn't read everything, but skimmed.

Looks like the file systems aren't mounted and the LVM subsystem isn't active.
run **sudo vgchange -ay** to have LVM scan for VGs and LVs, then you can do stuff with the mount options.

There are gvfs options that usually start with x- which can be added to the fstab mount line.  Something like x-show.... will make a partition show up separately in most Gnome GUI programs.  I don't know where it will show, since I don't use Gnome DE stuff or file managers.

Googled a bit ... x-gvfs-show is the option for the mount in the fstab.  No need to use UUIDs to mount LVs.  Use something like
/dev/{vg-name}/{lv-name} in the fstab where a device/uuid/label would be used.   There are links created by the mapper process automatically in that location for each LV.  For example, here's what it show for my VG named "hadar-vg"
```
$ ls -F /dev/hadar-vg/
libvirt-lv@      lv-regulus-2@  lv-vpn09-2004@  lv-zcs46@  swap_1@
lv-blog44-1804@  lv-spam3@      lv-xen41-1804@  lxd-lv@
lv-regulus@      lv-tp-lxd@     lv-zcs45-1804@  root@
```
The trailing '@' just means it is a symlink.

---

### Post by Dennis N on 2022-01-07
> I suppose p2 mentioned by you is my daily working PC, on which I just added a 500G SATA3 6G/s SSD.
I was referring to the NVMe drive shown in your output of post #8. There is an LVM partition nvme0n1p2 (which I referred to as p2). There are no logical volumes with Linux file systems showing, which is why it doesn't appear in your side pane or "Other Locations" in a file manager.

```
sda                     
&#9492;&#9472;sda1      ext4        
sdb                     
&#9500;&#9472;sdb1      vfat        /boot/efi
&#9492;&#9472;sdb2      ext4        /
nvme0n1                 
&#9500;&#9472;nvme0n1p1 vfat        
&#9492;&#9472;[COLOR="#FF0000"]**nvme0n1p2 LVM2_member**[/COLOR]
```

**_Added:_** read TheFu's explanation about the LVM subsystem not being active, and apply his remedy. That probably accounts for them not displaying as they normally would in Files.

---

### Post by satimis on 2022-01-08
> **TheFu said:**
> I didn't read everything, but skimmed.

Looks like the file systems aren't mounted and the LVM subsystem isn't active.
run **sudo vgchange -ay** to have LVM scan for VGs and LVs, then you can do stuff with the mount options.

There are gvfs options that usually start with x- which can be added to the fstab mount line.  Something like x-show.... will make a partition show up separately in most Gnome GUI programs.  I don't know where it will show, since I don't use Gnome DE stuff or file managers.

Googled a bit ... x-gvfs-show is the option for the mount in the fstab.  No need to use UUIDs to mount LVs.  Use something like
/dev/{vg-name}/{lv-name} in the fstab where a device/uuid/label would be used.   There are links created by the mapper process automatically in that location for each LV.  For example, here's what it show for my VG named "hadar-vg"
```
$ ls -F /dev/hadar-vg/
libvirt-lv@      lv-regulus-2@  lv-vpn09-2004@  lv-zcs46@  swap_1@
lv-blog44-1804@  lv-spam3@      lv-xen41-1804@  lxd-lv@
lv-regulus@      lv-tp-lxd@     lv-zcs45-1804@  root@
```
The trailing '@' just means it is a symlink.
$ sudo vgchange -ay```

sudo: vgchange: command not found
```
1
$ apt policy vgchange```

N: Unable to locate package vgchange

```

$ ls -F /dev/hadar-vg/```

ls: cannot access '/dev/hadar-vg/': No such file or directory
```

Ubuntu 20.04 on 1TB NVMe SSD HD was installed about 4 year ago running USB pen stick installer.  I selected using entire disk with LVM.  Ubuntu 20.04 is solely running as host of VirtualBox.  I haven't edited it since its installation except running update and upgrade periodically.  All works and tests are done on VMs

Until recently I need to test Video Editing software on bare-metal HD therefore I add this 500G SATA 6G/s SSD HD.  Ubuntu 20.04 was installed also running USB pen stick installer, selecting using entire HD without LVM

That is the complete story.

Regards

---

### Post by TheFu on 2022-01-08
If vgchange doesn't exist, then the system doesn't have LVM stuff installed.  Install it.
hadar-vg is MY VG, not yours.  I showed it as an example and showed the pattern above it.

Video software doesn't have anything to do with LVM.  This is straight disk mounting stuff with LVM.

---

### Post by satimis on 2022-01-08
> **TheFu said:**
> If vgchange doesn't exist, then the system doesn't have LVM stuff installed.  Install it.
hadar-vg is MY VG, not yours.  I showed it as an example and showed the pattern above it.

Video software doesn't have anything to do with LVM.  This is straight disk mounting stuff with LVM.
That was the output on Ubuntu 20.04 on 500G SSD HD

On 1TB NVMe PCIe 3.0x4 SSD HD

$ sudo vgchange -ay```

  /dev/sdc: open failed: No medium found
  /dev/sdc: open failed: No medium found

```

Again on 
$ lsblk -o name,fstype,mountpoint > lsblk.txt

Pls refer to attached file.

Thanks

Regards

---

### Post by TheFu on 2022-01-09
To save others from the hassle:
```
NAME                  FSTYPE      MOUNTPOINT
sda                               
&#9492;&#9472;sda1                ext4        
sdb                               
&#9500;&#9472;sdb1                vfat        
&#9492;&#9472;sdb2                ext4        
nvme0n1                           
&#9500;&#9472;nvme0n1p1           vfat        /boot/efi
&#9492;&#9472;nvme0n1p2           LVM2_member 
  &#9500;&#9472;ubuntu--vg-root   ext4        /
  &#9492;&#9472;ubuntu--vg-swap_1 swap        [SWAP]

```
So the vgchange command worked and you have ubuntu--vg-root which is mounted.
Nothing else shows any LVM.
If you want to mount sda1 or sdb2 (both are ext4), then either set a LABEL and mount using the LABEL= method in the fstab or look up the UUID for each and mount using the UUID= method.  I'm partial to the LABEL= method myself. Much easier for humans.  gparted will let you set a label ON THE PARTITION (not the disk).

BTW, a better command:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label
```
doesn't show the junk snap crap, and shows the other stuff of interest.

---

### Post by satimis on 2022-01-09
> **TheFu said:**
> To save others from the hassle:
```
NAME                  FSTYPE      MOUNTPOINT
sda                               
&#9492;&#9472;sda1                ext4        
sdb                               
&#9500;&#9472;sdb1                vfat        
&#9492;&#9472;sdb2                ext4        
nvme0n1                           
&#9500;&#9472;nvme0n1p1           vfat        /boot/efi
&#9492;&#9472;nvme0n1p2           LVM2_member 
  &#9500;&#9472;ubuntu--vg-root   ext4        /
  &#9492;&#9472;ubuntu--vg-swap_1 swap        [SWAP]

```
So the vgchange command worked and you have ubuntu--vg-root which is mounted.
Nothing else shows any LVM.
If you want to mount sda1 or sdb2 (both are ext4), then either set a LABEL and mount using the LABEL= method in the fstab or look up the UUID for each and mount using the UUID= method.  I'm partial to the LABEL= method myself. Much easier for humans.  gparted will let you set a label ON THE PARTITION (not the disk).

BTW, a better command:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label
```
doesn't show the junk snap crap, and shows the other stuff of interest.

In order to make my posting more clear, I re-arrange it as follows:-

1) On HD-1: 1TB NVMe PCIe Gen 3.0x4 SSD (running Ubuntu 20.04 for 4 years, solely as host of VirtualBox)
Run following commands on Terminal;

1a)
$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label```

NAME                  SIZE TYPE FSTYPE      MOUNTPOINT UUID                                   LABEL
sda                   3.7T disk                                                               
&#9492;&#9472;sda1                3.7T part ext4                   786a6a67-06f5-428f-a24d-fe75cd0b08d5   
sdb                 465.8G disk                                                               
&#9500;&#9472;sdb1                512M part vfat                   7735-7864                              
&#9492;&#9472;sdb2              465.3G part ext4                   f60e0b05-1944-402f-8029-81a9013711bc   
nvme0n1             953.9G disk                                                               
&#9500;&#9472;nvme0n1p1           512M part vfat        /boot/efi  0E3A-4ABA                              
&#9492;&#9472;nvme0n1p2         953.4G part LVM2_member            WmiqMV-mxBN-xNbz-WKk3-04Qm-OEvb-gfo2C6 
  &#9500;&#9472;ubuntu--vg-root 930.4G lvm  ext4        /          ef229efa-3019-4ba9-bddc-88c399244e99   
  &#9492;&#9472;ubuntu--vg-swap_1
                      976M lvm  swap        [SWAP]     ae829a93-d744-47b2-b378-85d58950c720   

```

1b)
$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=0E3A-4ABA  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```


2) HD-2: 500G SATA3 6G/s SSD (newly added, now running Ubuntu 20.04)
Run following commands on Terminal;

2a)
$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label```

NAME                    SIZE TYPE FSTYPE      MOUNTPOINT UUID                                   LABEL
sda                     3.7T disk                                                               
&#9492;&#9472;sda1                  3.7T part ext4                   786a6a67-06f5-428f-a24d-fe75cd0b08d5   
sdb                   465.8G disk                                                               
&#9500;&#9472;sdb1                  512M part vfat        /boot/efi  7735-7864                              
&#9492;&#9472;sdb2                465.3G part ext4        /          f60e0b05-1944-402f-8029-81a9013711bc   
nvme0n1               953.9G disk                                                               
&#9500;&#9472;nvme0n1p1             512M part vfat                   0E3A-4ABA                              
&#9492;&#9472;nvme0n1p2           953.4G part LVM2_member            WmiqMV-mxBN-xNbz-WKk3-04Qm-OEvb-gfo2C6 
  &#9500;&#9472;ubuntu--vg-root   930.4G lvm  ext4                   ef229efa-3019-4ba9-bddc-88c399244e99   
  &#9492;&#9472;ubuntu--vg-swap_1   976M lvm  swap                   ae829a93-d744-47b2-b378-85d58950c720 

```

2b)
$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=f60e0b05-1944-402f-8029-81a9013711bc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7735-7864  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

3) HD-3: 4TB WD HD, solely for data storage and without OS installed

Now
Starting HD-1, HD-2 can be mounted automatically for files sharing.

But
Starting HD-2, HD-1 can't be mounted automatically for files sharing.

How to fix the problem to mount HD-1 automatically on starting HD-2 ?

Regards

---

### Post by TheFu on 2022-01-10
You cannot mount the same storage to the exact same directory.  Mount the other partitions to some other, empty, directory.  Some where under /media is probably best.  Also, since they are used by alternate OSes, you might really want to use read-only mounts.

For pure data storage, I would mount them to the same location in all OSes involved.

Is this a trick question?  You've been here a long time and there are lots and lots of examples for fstab setups in the forums, plus there's a page at help.ubuntu.com which explains how the fstab works.  I've got to be missing something subtle that makes this hard.  The UUIDs are all different, so that isn't an issue.

I have no idea with HD-1, 2 and 3 are.  Maybe if you used the actual UUIDs that are shown in the lsblk output it would be clearer?

---

### Post by satimis on 2022-01-10
> **TheFu said:**
> You cannot mount the same storage to the exact same directory.  Mount the other partitions to some other, empty, directory.  Some where under /media is probably best.  Also, since they are used by alternate OSes, you might really want to use read-only mounts.

For pure data storage, I would mount them to the same location in all OSes involved.

Is this a trick question?  You've been here a long time and there are lots and lots of examples for fstab setups in the forums, plus there's a page at help.ubuntu.com which explains how the fstab works.  I've got to be missing something subtle that makes this hard.  The UUIDs are all different, so that isn't an issue.

I have no idea with HD-1, 2 and 3 are.  Maybe if you used the actual UUIDs that are shown in the lsblk output it would be clearer?

I'm now working on a spare PC which has been running at least 10 years. The same problem occurs here.  The newly added HDD, running Ubuntu 20.04, unable to mount the old HDD, also running Ubuntu 20.04, at starting the OS.

Details as follows:

HDD-1: 2TB SATA SSD, running Ubuntu 20.04(now) solely as host of VirtualBox.  All works are done on VMs
HDD-2: 2TB WD HDD solely for data storage
HDD-3: 2TB WD HDD solely for data storage
HDD-4: 500G SATA SSD, running Windows 10.  Added about 1 month ago
HDD-5: 250G SATA SSD, running Ubuntu 20.04.  Added about 1 month ago

[B]On adding a new HDD before installing OS, I un-pluged all other HDDs avoiding confusion.  After installation completed, other HDDs were re-connected.
[/B]

**[COLOR="#FF0000"]On HDD-1[/COLOR]**
$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label > lsblk-1.txt
(pls refer to lsblk-1.txt attached)

$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CC6D-6E39  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgubuntu-swap_1 none            swap    sw              0       0

```

**[COLOR="#FF0000"]On HDD-5[/COLOR]**

$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label```

NAME     SIZE TYPE FSTYPE      MOUNTPOINT UUID                                   LABEL
sda    465.8G disk ext4                   7f56d4de-0443-41de-ab44-e58ad4d247a3   
&#9500;&#9472;sda1   500M part ntfs                   A61E6D461E6D109B                       System Reserved
&#9500;&#9472;sda2 464.8G part ntfs                   A2B06EC8B06EA311                       
&#9492;&#9472;sda3   514M part ntfs                   20700CBA700C9924                       
sdb      1.8T disk                                                               
&#9500;&#9472;sdb1    16M part                                                               
&#9492;&#9472;sdb2   1.8T part ntfs                   FE58265758260EC9                       
sdc      1.8T disk                                                               
&#9500;&#9472;sdc1   512M part vfat                   CC6D-6E39                              
&#9492;&#9472;sdc2   1.8T part LVM2_member            WLJcOs-IsZN-P1Vp-tG1n-nmGt-BQaI-2BF9EI 
sdd      1.8T disk                                                               
&#9492;&#9472;sdd1   1.8T part ext4                   eee0a8e0-4ac5-433e-b6e0-9cbf67916666   
sde    232.9G disk                                                               
&#9500;&#9472;sde1   512M part vfat        /boot/efi  5DFD-253C                              
&#9500;&#9472;sde2     1K part                                                               
&#9492;&#9472;sde5 232.4G part ext4        /          2fc7a0c1-f447-46b1-ba7c-ebc7a7ec9bf2   
sr0     1024M rom                                                               

```

$ cat /etc/fstab```
 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2fc7a0c1-f447-46b1-ba7c-ebc7a7ec9bf2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5DFD-253C  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

Regards

---

### Post by TheFu on 2022-01-10
You post 5 HDDs and label them HDD-5.  Which 1 is it?
Can you not just use the UUID for each partition?  I'm so confused.  Seems like the target keeps moving.

---

### Post by satimis on 2022-01-10
> **TheFu said:**
> You post 5 HDDs and label them HDD-5.  Which 1 is it?
Can you not just use the UUID for each partition?  I'm so confused.  Seems like the target keeps moving.
The PC with 5 HDDs is a spare PC, as for example only.  I mentioned it just indicating that this spare PC also having similar problem.

The PC with 3 HDDs is the PC mentioned at the beginning of this posting.

Regards

---

### Post by TheFu on 2022-01-10
If you will list 
[LIST]
[*]the UUID/Label for the partition, 
[*]the location where you want it mounted and 
[*]the file system type, 
[/LIST]
then an fstab line can be easily created for each file system.

If the storage is using LVM, then list the path to the LV .... like /dev/{vgname}/{lvname} which will be an existing symlink rather than the LABEL or UUID.

Please.

[Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) has a prior "how-to" for ext4.

---

### Post by satimis on 2022-01-12
> **TheFu said:**
> If you will list 
[LIST]
[*]the UUID/Label for the partition, 
[*]the location where you want it mounted and 
[*]the file system type, 
[/LIST]
then an fstab line can be easily created for each file system.

If the storage is using LVM, then list the path to the LV .... like /dev/{vgname}/{lvname} which will be an existing symlink rather than the LABEL or UUID.

Please.

[Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) has a prior "how-to" for ext4.

Hi TheFu,

Something funny happened here.  Now 500G SATA3 SSD can connect 1TB NVMe PCIe Gen3.0 SSD.  I haven't done anything on both of them.

Recently I added a 1TB SATA3 SSD and installed Windows 10 on it.  Before installation I disconnected all other HDDs.  After installation completed I re-connected all HDDs.  On starting Ubuntu 20.04 on 500G SSD, 1TB NVMe SSD can be automatically mounted.  Now on 500G SSD, 1TB NVMe SSD can be connected for files sharing.

The remaining solution for me to solve it how to have 1TB NVMe SSD, 500G SSD and 4TB WD HDD connected on Windows 10 ?

Regards

---

