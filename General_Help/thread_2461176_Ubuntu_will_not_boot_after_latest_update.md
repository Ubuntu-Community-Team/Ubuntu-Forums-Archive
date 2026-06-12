---
title: "Ubuntu will not boot after latest update:"
date: 2021-04-25
forum: General Help
---

### Post by TheMustangZone on 2021-04-25
I was having no issues and installed the latest update the other day.  Now, my computer will not boot into Ubuntu.  I do not use Windows, so no dual boot.  I used an install CD and ran Boot-Repair, but it did not fix anything.  It gave me the link below.  Any help would be appreciated, as I don't want to lose my data.

  	 	 	 	   [https://paste.ubuntu.com/p/r7DC6mkMbV/](https://paste.ubuntu.com/p/r7DC6mkMbV/)

---

### Post by oldfred on 2021-04-25
You show two drives, one gpt and one MBR.
The gpt drive has one ext4 partition.
The MBR drive has grub, but it is trying to boot from partition 1 which you do not have. Partition one on sda, does not exist and partition 1 on sdb is the extended partition.

Did you change partitions around?
Report also did not show any internals like fstab. Does partition need fsck?
Why an NTFS partition if no Windows. It typically needs chkdsk or defrag periodically and you cannot do that from Linux.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda2

For grub to install to sda, you need a tiny 1 or 2MB unformatted partition with the bios_grub flag (if using gparted).

---

### Post by HermanAB on 2021-04-26
Hi Fred,

Before faffing with partitions and boot, *first backup your data!*  

You can do that with an install CD / USB widget. 
Once booted up, mount (just a clicketyclick with the file manager) the disk partitions one by one and look around for your data.  
When you find it, save it.
Once your data is safe, you can relax and figure out how to fix your system.

I usually prefer a quick re-install, since it is much faster than fixing a wonky system and then I have the latest and greatest version, so what is not to like about it?

---

