---
title: "Suggestion for partitioning drive for multiple distros"
date: 2018-07-26
forum: General Help
---

### Post by atom-101 on 2018-07-26
I have a 500gb ssd on which I plan on running three distros, Ubuntu, Fedora and Kali. What I want to set up is a way to have all of these distros have a common partition for data. I thought I would have a common home partition for all distros but apparently that is not a good idea as it can break stuff.

So, here's what I am hoping to accomplish:
I want a common boot partition for all distros. I'm guessing about 400mb should be enough. 
150mb for the efi partition.
I will install the root of each distro in a separate partition, which will be kept as small as possible, but will have healthy room for updates. 
Then I will have a large partition for common data.
(I want the root and data partitions to be using LVM)

Also, I have a 120gb ssd lying around that I can add to this build. I am guessing that I can easily create logical volumes that can exist across the physical discs. My question here is that, if the 120gb drive has a part of a logical volume, and it is not available during boot(only the part on the 500gb drive is present), will I be able to use my PC without data loss?

I am looking for suggestions regarding how big I should keep the root of each distro. Please tell me the sizes I should keep for physical volumes and logical volumes. I am not too well versed with lvms.

---

### Post by Dennis N on 2018-07-26
Great Project!

Using new LVM and manual setup, you need:

1) EFI system partition. Mine are 80 MB.
2) One partition formatted as LVM Physical Volume (gparted can do this)
3) One volume group (VG) using the physical volume. (you need terminal commands to create it).
4) For each OS, a logical volume (LV) within the volume group volume mounted as /. (you need terminal commands to make them). I make new LVs with size 3500 extents, about 14 GB. You can expand them as needed.
5) swap partition because Fedora will want one (I use a regular partition).

I am 99% sure you can't use a common boot partition. You don't need any boot partition for Ubuntu or Fedora; I don't know about Kali. Only reason to have a boot partition with newest grub is if the disk is encrypted, I think. 

I am slowly converting my sdb disk shown to LVM - if I replace an old OS, I first convert the partition to a LVM physical volume and add it to my VG. Then I install replacement OS in a LV.

```
dmn@Sydney:~$ lsblk -o name,fstype,label
NAME                    FSTYPE      LABEL
sdb                                 
&#9500;&#9472;sdb1                  vfat        EFI System Partition
&#9500;&#9472;sdb2                  ext4        Manjaro-XFCE
&#9500;&#9472;sdb3                  ext4        Manjaro-MATE
&#9500;&#9472;sdb4                  vfat        
&#9500;&#9472;sdb5                  LVM2_member 
&#9474; &#9500;&#9472;os_vg-mint_xfce     ext4        Mint-XFCE
&#9474; &#9500;&#9472;os_vg-mint_mate     ext4        Mint-MATE
&#9474; &#9500;&#9472;os_vg-fedora_gnome  ext4        Fedora-GNOME
&#9474; &#9492;&#9472;os_vg-umate         ext4        Ubuntu-Mate-1804
&#9500;&#9472;sdb6                  vfat        EFI System Partition
&#9492;&#9472;sdb7                  LVM2_member 
  &#9500;&#9472;os_vg-ubuntu_gnome  ext4        Ubuntu-1804
  &#9492;&#9472;os_vg-manjaro_gnome ext4        Manjaro-Gnome


```
My first physical volume was sdb5, and the volume group is os_vg. Then, when it ran out of room, I added sdb7 to os_vg and installed two more OS. If I ever replace the Manjaro on sdb2 or sdb3, I would add the partition to os_vg.

If you're wondering, swap is on sda (not shown) along with a big data partition.

Your question:

If your VG is split between two physical disks and one is missing, it probably won't boot. I make a new VG for a 2nd disk.

---

### Post by atom-101 on 2018-07-27
Thanks for the detailed response.  :)
I have a few questions:
Why do you have two efi partitions?
Are you positive that it is safe to keep boot on LVM? All tutorials I have seen, do not recommend this. The argument is that this does not create performance issues, but troubleshooting issues. 
Why will Fedora want a swap? I have 16gb of RAM so is it necessary? That said, Fedora is the only one out of the three distros that I haven't used before. 

I am now planning to use the 120gb drive as a vanilla ext4 data partition, without LVM.

---

### Post by Dennis N on 2018-07-27
> Why do you have two efi partitions?
There are 3 on sdb: sdb1, sdb4, sdb6. Yet another ESP (EFI system partition) is on sda because Ubuntu will only install to an ESP on sda, and secondly, in case sdb disk fails I can still boot my system to an OS I have installed on sda (sda is not shown in the display of my previous post).

I don't really need three ESP on sdb - it was an experiment done when UEFI first came out to see if two or more ESPs could work on the same disk. Many things about UEFI and the possibilities were not clear when it first showed up around 2012. Otherwise more than one ESP can be useful if you install 2 OS of same type (like two Ubuntu versions) and you want both bootable from the UEFI boot menu (for that to be possible, they need separate ESPs). Once I had Korora and Fedora installed, and they needed separate ESPs because of how I boot them. 

With two Ubuntu, the second Ubuntu's ESP files will overwrite those of the first Ubuntu using the ESP on sda. That's usually OK, since you can still boot the first Ubuntu from Grub of another OS.   

> Are you positive that it is safe to keep boot on LVM?
Yes. I don't have any boot partitions. This works with newer grub versions (probably since Ubuntu 14.04?). Before that I think you did need the boot partition outside of LVM structure.  

> Why will Fedora want a swap? I have 16gb of RAM so is it necessary?
You may not need one, but some installers insist you specify one or they will not install the OS. Newer Ubuntu will make a swap file if no swap partition is on the disk. I believe Fedora will warn you, but let you install without any swap. Don't know about Kali - never used it.

> I am now planning to use the 120gb drive as a vanilla ext4 data partition, without LVM. 
Good choice. My data partition is on sda and is a regular ext4 partition (no LVM). 

Have fun with your new LVM!

---

