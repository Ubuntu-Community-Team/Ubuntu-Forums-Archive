---
title: "Problem on upgrade hard drive"
date: 2022-11-25
forum: General Help
---

### Post by satimis on 2022-11-25
Hi all,

Ubuntu 22.04
Oracle VirtualBox

My old 1TB NVMe Gen3 SSD ran short of space. I purchased a new 2TB NVMe Gen3 SSD to replace it.  First I cloned the old 1TB NVMe Gen3 SSD on 2TB NVMe Gen3 SSD running "pvmove".  Before cloning I ran dd to backup the entire 1TB NVMe Gen3 SSD as image.

Cloning went through without problem but after finish I couldn't start the system on the new 2TB NVMe Gen3 SSD.  Then I restored the backup image on the new 2TB NVMe Gen3 SSD.  But following problems were encountered;

1) The system only took up half storage space of the new 2TB NVMe Gen3 SSD.  I couldn't use the remaining 1TB storage space.
2) The old 1TB NVMe Gen3 SSD and the new 2TB NVMe Gen3 SSD couldn't be installed in the PC at the same time.  Otherwise booting Ubuntu 22.04 on new 2TB NVMe Gen3 SSD it booted to grub command line screen instead of Grub menu.

Then I made a clean installation running 20.04 USB installer (at that time I didn't have an Ubuntu 22.04 USB installer) to install Ubuntu 20.04 on the new 2TB NVMe Gen3 SSD and upgrade it to Ubuntu 22.04.  Again the old 1TB NVMe Gen3 SSD and the new 2TB NVMe Gen3 SSD couldn't be installed in the PC at the same.  Otherwise booting Ubuntu 22.04 on new 2TB NVMe Gen3 SSD it booted to grub command line screen instead of Grub menu.

Afterwards I installed following packages;
1) Oracle VirtualBox - installed on the package download on Oracle website
2) Firefox - running Flatpak
3) Google Chrome - 
How to install google chrome on Ubuntu 22.04
Method 2: Install Google Chrome using Google repository
[https://itslinuxfoss.com/install-google-chrome-ubuntu-22-04/](https://itslinuxfoss.com/install-google-chrome-ubuntu-22-04/)

All 3 packages have problems
e.g.
1) VM icons on the left vertical menu bar of Ubuntu 22.04 missing
2) Browsing websites on Internet it shows a small website (zoom at 100%). I need to expand zoom to 175%) (see screenshot attached)
3) Again the old 1TB NVMe Gen3 SSD and the new 2TB NVMe Gen3 SSD couldn't be installed in the PC at the same time.  Otherwise booting Ubuntu 22.04 on new 2TB NVMe Gen3 SSD it boots to grub command line screen instead of Grub menu.

etc .

I'm prepared to make a clean installation of Ubuntu 22.04 on the new 2TB NVMe Gen3 SSD the 2nd time.  Now I have Ubuntu 22.04 USB installer.

Please advise what attention I must pay to?

Remark:
Fortunately the other hard drives on this PC are without infected
500G SATA3 SSD - running Ubuntu 22.04 and KVM
1TB SATA3 SSD - running Windows 11
4TB WD Hard drive - ext4, solely for storage without OS installed.

Thanks in advance.

Regards

---

### Post by TheFu on 2022-11-25
Likely that cloning tools also cloned the UUIDs for each drive and partition.  Change those and update the UUIDs in the fstab.  I'm afraid to say anything more, since my posts seem to cause you more problems for some reason.

---

### Post by satimis on 2022-11-25
> **TheFu said:**
> Likely that cloning tools also cloned the UUIDs for each drive and partition.  Change those and update the UUIDs in the fstab.  I'm afraid to say anything more, since my posts seem to cause you more problems for some reason.
Never mind.  Your intention was trying to help me.  It is a good intention !

I'm curious to know why 2 NVMe SSDs  can't be installed at the same time ? Just for curiosity!

If the 2nd clean installation still fails I'll turn to install all data on the new PC.  I have been planning to build a new AMD Ryzen 9 7900X or 7950X PC.  Unfortunately the motherboard is quite expensive.  I'll wait until after new year 2023.

Regards

---

### Post by TheFu on 2022-11-25
Duplicate UUIDs aren't allowed.  Thought that was clear from my post above.
Also, some motherboards have slots for 2 NVMe devices, but only 1 can be used depending on the other PCIe slots used.  That is a motherboard thing. Read the motherboard manual for more.  I'd provide an example, but it would likely be too confusing.

---

### Post by satimis on 2022-11-25
> **TheFu said:**
> Duplicate UUIDs aren't allowed.  Thought that was clear from my post above.
Also, some motherboards have slots for 2 NVMe devices, but only 1 can be used depending on the other PCIe slots used.  That is a motherboard thing. Read the motherboard manual for more.  I'd provide an example, but it would likely be too confusing.
Thanks for your advice.  I won't put further effort to find it out.

Restoring the 1TB disk image on the new 2TB NVMe SSD works but I have to sacrifice the remaining 1TB storage space.

Anyway I'll try to make another clean installation to see what will happen ?  I create this post solely in anticipation seeking advice on points I have to pay attention to,

Regards

---

### Post by ajgreeny on 2022-11-25
Have you tried increasing the size of the 1TB volume using gparted on a live system as it seems obvious to me that cloning a 1TB volume and copying it to another disk will, of course, still be only 1TB; after all, it's a clone!

I have no experience of doing anything like this, so make doubly sure you still have the original before trying to enlarge the clone or you could end up with neither.

---

### Post by satimis on 2022-11-25
> **ajgreeny said:**
> Have you tried increasing the size of the 1TB volume using gparted on a live system as it seems obvious to me that cloning a 1TB volume and copying it to another disk will, of course, still be only 1TB; after all, it's a clone!

- snip -
Thanks for your advice.

I don't think having another chance to clone the old 1TB NVMe SSD again.  It seems to me damaged.

Fortunately I have performed following steps before running "pvmove" to clone the old 1TB NVMe SSD
1) Ran dd to backup the entire old 1TB NVMe SSD as backup image
2) Had following files/data copied to the 4TB SATA3 storage hard drive
a) AppImages: such as gimp, shotcut, openshot, avidemux etc.
b) VirtualBox VM .vdi images
c) Working data

I'm considering to perform following test;
1) Run Ubuntu 22.04 USB installer with "fdisk" to erase the new 2TB NVMe Gen3 SSD and create the entire SSD as .ext4 format without partition
2) Restore the backup image again on the new 2TB NVMe Gen3 SSD
to see what will happen ?

Your comment and advice would be appreciated

Regards

---

### Post by #&amp;thj^% on 2022-11-25
Test the back-up first. That may require the use of another drive though. (just thinking off the top of my head)
My thought's are to save unnecessary writes to SSD Flash drive.

---

### Post by satimis on 2022-11-25
> **1fallen said:**
> Test the back-up first. That may require the use of another drive though. (just thinking off the top of my head)
I only have 2 NVMe SSDs, the old 1TB NVMe SSD and the new 2TB NVMe SSD.  I'm prepared using the new SSD for this test.  I don't have a 3rd NVMe SSD
> 
My thought's are to save unnecessary writes to SSD Flash drive.
Could you explain in more detail? What shall I perform?

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-11-25
> **satimis said:**
> I only have 2 NVMe SSDs, the old 1TB NVMe SSD and the new 2TB NVMe SSD.  I'm prepared using the new SSD for this test.  I don't have a 3rd NVMe SSD

I would think that would be safe for a first write. I'm probably just making noise here.
> **satimis said:**
> 
Could you explain in more detail? What shall I perform?

Thanks

Regards
They only have (X) amount of writes for a life span as in this example:
> An SSD that stores two bits of data per cell, commonly referred to as multi-level cell (MLC) flash, generally sustains up to 10,000 write cycles with planar NAND and up to 35,000 write cycles with 3D NAND
Like I said I'm just making a little noise, sorry for throwing you in another direction.

---

### Post by satimis on 2022-11-27
Hi all,

Tried again;
Restore old 1TB NVMe SSD disk backup image on new 2TB NVMe SSD

First ran fdisk create a single partition on new 2TB NVMe SSD

Then run;
$ sudo mkfs -t ext4 /dev/nvme0n1 ```

mke2fs 1.46.5 (30-Dec-2021)
Found a dos partition table in /dev/nvme0n1
Proceed anyway? (y,N) y [enter]

Discarding device blocks: done                            
Creating filesystem with 488378646 4k blocks and 122101760 inodes
Filesystem UUID: cb24f222-2f0c-45d2-b785-f0b6b8e44f6e
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done

```

Run dd to Restore the disk backup image```

$ sudo dd if=/media/satimis/786a6a67-06f5-428f-a24d-fe75cd0b08d5/1tb_ssd_backup.img of=/dev/nvme0n1 bs=64

```

It took more than 5 hours without finish.  Finally I have to reboot the PC

Regards

---

