---
title: "Partitioning not possible"
date: 2018-12-12
forum: General Help
---

### Post by hennmann on 2018-12-12
I have an Acer Aspire One 533 with a Western Digital  1 TB SSD currently running Win7Pro 64
The SSD currently has:
1 FAT32 13.01 Gb Recovery Partition (set up originally by Acer to reinstall or repair Windows due to lack of DVD drive)
1 NTFS 375gb empty partition
1 NTFS 302gb empty partition

1 NTFS 245gb  Windows Win7/64 Pro partition consisting of:
      1 NTFS 100.3 Mb System Partition (basically Windows Boot Partition)
      1 NTFS 992.50 Kib System Reserved
      1 NTFS 243.95Gib Main Windows 7 Partition

NOW given that this is a 1 TB drive with considerable room for this modest Acer Netbook and NOT a 10, 20, 0r 30 GB like on my older Laptops I wanted 
a separate 375 GB partition for storage of files
a separate 300 (give or take) partition to install a Linux OS

In Ubuntu 18.0.4.1, Lubuntu 18.10, and Debian 9.4.6.0 AMD64, GParted, KDE Partition Manager see the two empty partitions as 674.36 unallocated
In Windows Management This hard drive is Recognized as having the usual slew of Windows Partitions set up during installation AND my 2 partitions formatted and set up  as NTFS 

When I try to install Debian, Ubuntu, Lubuntu, the partitioning tools such as KDE Partition Manager, GParted quite simply SNIVEL that I have the maximum amount of partitions and simply will not allow me to set up the 2 partitions I wanted in the first place, the NTFS empty storage partition and the partition for Linux! Now I look at 674.36 just simply sitting there being declared unallocated.

What do I have to do to resolve this situation? Deleting the Windows partition with all of it's system partitions quite simply isn't an option as I want dual boot and at the present time I have no intentions of deleting the OEM recovery partition.
When I replaced the slow mechanical hard drive with the new solid state drive I used the cloning software to properly transfer over the Acer recovery partition and all of it's bootable contents so it would perform as it originally did. Until I fully understand, accept, and fully use Linux of whatever flavor I decide in and only have Linux on the hard drive, then I will pull the plug on Windows.

---

### Post by l33ch on 2018-12-12
Not sure if this applies but for MBR partitioning schemes you are limited to creating a maximum of 4 primary partitions.

You can install Linux anywhere. Doesn't have to be a primary partition, it can be in a logical partition as well. In fact on this system I'm using right now:

500GB HDD
sda1 = ntfs system reverved 100mb
sda2 = ntfs win7 system partition 365GB
sda3 = ext4 primary 60gb (linux)
sda4 extended partition:
sda6 linux swap 1.5gb
sda5 ntfs 45gb data partition.

So my linux swap and 45gb ntfs data partition are located within a logical extended partition.  I think I'm using 3 Primaries and 1 Logical (which counts as a primary..but not the partitions contained within that extended partition), so 4. Unlike winbloze (when it comes to boot/system partitions, data partitions it don't matter),  linux trully doesn't give a damn as long as it knows where to find the partitions (as set up via installation / /etc/fstab).
Hope that helps.

---

### Post by oldfred on 2018-12-12
Post this from live installer:
sudo parted -l
sudo fdisk -lu

Windows 7 typically was installed in BIOS boot mode with MBR (msdos) partitioning which has the 4 primary partition limit.
Only a few newer Windows 7 systems were in UEFI boot mode, but Windows 7 did not support UEFI secure boot mode. If UEFI, Windows requires gpt partitioning.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by hennmann on 2018-12-13
Let me shed a bit more light on the situation. 
This pathetic little Acer originally had Win7 Starter on the 250 Gb drive. Ripped it out along with the sick joke of 1gb of RAM making an already enemic version of Widoze struggle like a two legged dog. I stuck in a stick of 2gb, this 1Tb SSD, reinstalled 7 Starter Edition and also setup 3 partitions, one for 7, one for 10 and one for Linux. When I installed 10 it overwrote the 7 boot manager and provided a Win 10 boot manager giving me the option of either/or. Win7 starter became like a 3.5 legged dog after the RAM and SSD meanwhile Win 10 was like a 2 legged dog with a broken leg. Along comes Ubuntu so I figured lets install on the 3rd partition. No sniveling about more than 4 partitions, allowed me to set up /,/home, swap (yes swap, don't forget pathetic amount of RAM!). It left everything intact including my new partition scheme for Ub and I selected the 134 meg Win 10 partition for the Grub boot manager and rebooted. Now we are greeted with a Grub menu with everything looking like it should but Win7&10 would not boot. Well what the heck so I ripped out 10, reinstalled 7 as Win 7Pro/64 and partitioned the 1Tb as it was with an empty NTSF and a third NTFS for Linux with the above said problem. Should I have partitioned and formatted as Fat32? Most info I read mentioned NTFS works fine for both Win and Lin to access??? Is this the " fly in the ointment" why things are not working? It puzzles me that even though Win 7 sees 3 NTFS partitions Linux sees one with the Windows setup(system reserved etc. ) and my two partitions are now recognized as a lump sum of allocated not formatable or able to be partitioned. This is the before and after

---

### Post by l33ch on 2018-12-13
I think the m$atan system reserved partition  (which is flagged as hidden I believe?) is fat32 and not ntfs. That is for the the system reserved 100mb partition.  Not NTFS.  You could try restoring the windows 10 stock bootability (and its ability to load win7) via the  DVD/rescue disc/win10 USB install ([https://neosmart.net/wiki/fix-mbr/#Fix_the_MBR_in_Windows_10](https://neosmart.net/wiki/fix-mbr/#Fix_the_MBR_in_Windows_10)) so you can get those back up and running, then re-attempt a correct/compatible partitioning scheme to install linux. Apologies ahead of time if this/I am of no help. Good luck.


* Also, when it asked me where to install grub, I just had it install on the 1st hdd disk and not any individual partition. It will overwrite the windows bootloader, but grub will/should find windows 10 and windows 7 with linux as the default. Or, it will show windows 10, and linux as the default, but if you select windows 10 it will bring up the windows 10 boot loader with option to boot windows 7 (chainloading). But, I think it's usually better to install it on the mbr on the 1st hard disk (the default..no particular partition).

---

### Post by yancek on 2018-12-13
> a third NTFS for Linux with the above said problem. Should I have  partitioned and formatted as Fat32? Most info I read mentioned NTFS  works fine for both Win and Lin to access??

A Linux system will not run/work on a windows (ntfs) formatted drive.  It can be used to access 'data' from both windows and Linux but the system partition for Linux needs a Linux filesystem just as a windows install needs a windows filesystem.

I would be usesful for members to help you if you posted the output of the commands suggested by oldfred above.

---

### Post by hennmann on 2018-12-13
UEFI isn't an issue here oldfred as this Acer has BIOS and simply put MBR supports only 4 partitions so the story goes. 

I played around created the usual 3 partitions using GParted after deleting all of the Windows partitions and options were limited (no surprise)made a hasty retreat BEFORE installing Lubuntu and finally reinstalled Windows 7 Home Premium 32 because it is a little bit lighter than the Pro and 2 GB isn't much for 64.
When Win 7 was reinstalled with all the drivers updates etc. I checked BIOS version to discover a much newer version was available and reflashed the BIOS.
Not much was different except there was the option to select AHCI so instead of  nothing ventured, nothing gained and selected this.

Okay next we got to Windows Manager and the usual system partitions added to the previously GParted created partitions except in GParted I selected Fat32 but in Windows Management I formatted them both to NTSF. After all yes yancek Linux cannot run in NTFS but we can transfer files back and forth in this file system and if and when I get this sorted out I can set up one of the partitions into the proper partition table for Linux.

Windows didn't complain about more than 4 partitions so off to Rufus we go and I selected Lubuntu 18.04.1-desktop-i386 the 32 bit version. 
Installation is ticking along smoothly and now we are entering the installing variations so at first I selected the first option "install Ubuntu beside Windows" but it indicated two slightly smaller partitions than what I created so I selected the partitioning tool at this point.  Now we are greeted with exactly what I created in the first place with the recovery partition also indicated, selected the second partition I created for the installation location and selected install now. A window pops up "no / partition selected" so I hit the back button and selected the Linux partition and create. Okay I selected 50GB for / and the circle rotated...........bing bang boom! We have another partition and no snivel. Well if this worked (fingers crossed at this point) lets make another so swap it is of the size 4gb because of the pathetic amount I have and oh we are happy again so I put the rest 200GB into a /home.........my my my we have /, swap, /home on top of the other 3 clearly a violation of MBR but installation continues to the reboot and what a fine looking Grub bootloader we have, select Windows, Windows is alive and well, boot into Lubuntu and all is well there as well. Firefox is a bit sluggish opening but I forget about this at the moment and perform the updates and this is now happening.

This is pretty much what has happened after reading the links oldfred posted.

The difference being the 18.04.1-desktop-i386/32
Win7/32 Home Premium
And an updated BIOS version

As for Firefox well other members mentioned these Web browsers tend to suck alot of RAM but otherwise performance is very good, not quite as fast as Puppy but is probably better for software, updates, etc. being LTS seems to me?
Otherwise I have no idea what worked, (BIOS flash? different software?0 this time but if it ain't broke don't fix so I will leave it.

---

### Post by hennmann on 2018-12-13
l33ch now that you mention it yes I stumbled across the Win 10 workaround for UEFI and BIOS but, well, hmmmm I thought this isn't Windows 10 after giving this alot of thought even looking into Hybrid setup but there were mentions of this setting up ones self for a fall.
In the accessories>disks  my partitions appear as
PQSERVICE (that recovery partition)/Filesystem Partition 2 268 GB NTFS (Win7)/Filesystem Partition 3 50 GB EXT4 (my /)/Extended Partition Partition 4 668 GB             and in this Extended Partition is my Swap (partition6), Filesystem Partition 214 GB/home, and finally the New volume Partition 5 449 GB NTFS.
Also in Lubuntu the 449 GB isn't showing up in the file location like Ubuntu and in Disk it is indicating unmounted.

---

