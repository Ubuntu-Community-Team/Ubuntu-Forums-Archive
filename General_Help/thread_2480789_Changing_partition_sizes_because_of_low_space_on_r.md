---
title: "Changing partition sizes because of low space on root"
date: 2022-11-10
forum: General Help
---

### Post by zmarko on 2022-11-10
I installed Ubuntu 22.04 LTS alongside Windows 10 on my computer, and I followed [this tutorial]("https://medium.com/linuxforeveryone/how-to-install-ubuntu-20-04-and-dual-boot-alongside-windows-10-323a85271a73"), as it was recommended on Ubuntu website. The size of my root partition is 16gb, and now it already has only like 300mb of free space, so now I'm pretty sure it's just easier to have everything in the same partition. Do I have to delete Ubuntu, format partitions and install it again or is there some easier way to do this?

If I have to reinstall Ubuntu, what is the safest way to do it?

---

### Post by oldfred on 2022-11-10
You always should have good backups, to make it easy to reinstall when drive fails or you want new larger/faster drive.
Backup at minimum should include /home, list of installed apps & any system settings you change in /etc. I change grub files, but save copies in /home for backup. If you have installed server type apps those also need backup, usually in / somewhere.

Ubuntu now needs more space. Snaps take a lot of room. I do uninstall snaps and use Kubuntu  and my current / is 15GB, but I save all data normally in /home in separate data folders like documents, Pictures, etc on my second drive in a data partition and mount it back into / & link to folder in /home.

Depending on where other partitions are on drive, you may be able to expand. But you always expand a partition into space on the right when using gparted from live installer. If shrinking a large partition on left, and moving a partition left, it can take a while as all data must be copied. Any interruption corrupts the partition, so reason for good backups.

Post these:
sudo fdisk -lu
lsblk -f

---

### Post by nickdc on 2022-11-10
It shouldn't be necessary to reinstall Ubuntu. An application called GParted, available through the Ubuntu Software app (which itself comes ready installed and is on your menu), is a very reliable tool for managing all sorts of partition related tasks. It will show you a graphical representation of all your drives and the partitions on each and you can use it to resize the partition on which you've installed Ubuntu. You may need to first shrink the partition containing Windows in order to create some extra space. There's a lot of guidance out there for using GParted; best read up on it before proceeding, as mistakes in making partition changes can cause a lot of grief.

---

### Post by zmarko on 2022-11-10
Thanks for the reply! I didn't even install much stuff so I don't really need the backups.
Here is the output:

sudo fdisk -lu:
```

Disk /dev/nvme0n1: 238,47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: INTEL SSDPEKKF256G8L                    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EB0FE4C1-69E9-4418-ACB4-5B1A8C81D90B

Device             Start       End   Sectors  Size Type
/dev/nvme0n1p1      2048    206847    204800  100M EFI System
/dev/nvme0n1p2    206848    239615     32768   16M Microsoft reserved
/dev/nvme0n1p3    239616 396671628 396432013  189G Microsoft basic data
/dev/nvme0n1p4 499073024 500115455   1042432  509M Windows recovery environment
/dev/nvme0n1p5 396673024 412671999  15998976  7,6G Linux swap
/dev/nvme0n1p6 412672000 444671999  32000000 15,3G Linux filesystem
/dev/nvme0n1p7 444672000 499073023  54401024 25,9G Linux filesystem

Partition table entries are not in disk order.




```

lsblk -f:
```

NAME        FSTYPE   FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS

sda                                                                                  
nvme0n1                                                                              
&#9500;&#9472;nvme0n1p1 vfat     FAT32       86C9-7F52                              65,8M    31% /boot/efi
&#9500;&#9472;nvme0n1p2                                                                          
&#9500;&#9472;nvme0n1p3 ntfs                 D460CDCC60CDB590                                    
&#9500;&#9472;nvme0n1p4 ntfs                 60E0DB56E0DB3150                                    
&#9500;&#9472;nvme0n1p5 swap     1           1f50fcca-7414-4833-9da6-0ffc8683c4a8                [SWAP]
&#9500;&#9472;nvme0n1p6 ext4     1.0         f35ed91a-a87c-408f-933c-88c7714c1ba1    1,8G    83% /var/snap/firefox/common/host-hunspell
&#9474;                                                                                    /
&#9492;&#9472;nvme0n1p7 ext4     1.0         2927bdd0-ec5c-4aee-a162-d726a39b5e19   22,1G     8% /home

```

---

### Post by VMC on 2022-11-10
Some cleaning might be in order. My Ubuntu rarely goes past 6gb. See if you have multiple linux installed. I'm with oldfred in that I remove Snap.
edit: To see how many linux could be removed, run this from a terminal. Note:some believe in having two linux as backup. I only run with one.
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```

---

### Post by oldfred on 2022-11-10
Removed loop devices which are just all the snaps. 

It looks like Windows is hibernated, fast start up on, or has bitlocker on. It does not show size nor use of the NTFS partitions.
If shrinking NTFS, only use Windows and make sure you leave at least 30% unused as NTFS slows if not lots of extra space.

You do not need 8GB swap. Default install is now 2GB as a file in /.
Hibernation is not recommended and that would be the only time you would need 8GB. With NVMe drive full boot is almost as fast or maybe even faster than hibernation.

Both / & /home are not large, but that depends on what you install in the way of applications and how much data you save.
Back with XP years ago I had a NTFS data partition for some data to share between systems & Linux data partition for Linux data.
Now Windows makes it a bit more difficult as fast startup/hibernation and bitlocker must be off for the Linux NTFS driver to be able to see NTFS partitions.

One alternative is to remove swap partition & edit fstab to remove mount of swap. Comment swap line in fstab with # first (so later you can update UUID & uncomment), then boot live installer and with gparted remove swap & move / left & expand right. If also further shrinking Windows, you can move further left. If you want swap you can move /home left, & add new swap partition of 2GB. Then update fstab with new UUID of new swap.
But sizes you may need or want will totally depend on your use of Ubuntu.

---

### Post by ActionParsnip on 2022-11-10
What is the output of:
```

df -h

```

---

