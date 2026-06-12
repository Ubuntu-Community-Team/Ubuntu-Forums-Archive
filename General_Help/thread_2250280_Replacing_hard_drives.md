---
title: "Replacing hard drives"
date: 2014-10-27
forum: General Help
---

### Post by Bat_Phil on 2014-10-27
Hello

I am a relatively new Linux user looking for a lilttle assistance. I am running a Kubuntu system with 2 hard drives - the first (smaller) drive holds the Linux system, whilst a larger drive holds the /home partition.

Having now acquired a larger drive, I now want to:

1. Delete any existing partitions on my new drive and create a single new partition.
2. Format the new partition using the ext4 file system.
3. Copy the existing /home partition onto the new drive (including the hidden folders that hold user settings, etc.).
4. Replace the existing /home drive with the new one.


Please can somebody explain how best to achieve what I want so that evrything works seemlessly.

Many thanks in advance
Phil

---

### Post by oldfred on 2014-10-27
You can create new partition and format as ext4.
Do you really want entire drive as one large partition. New drives often are very large and often smaller partitions may be better. Only if storing Videos or other large files may it make more sense just to have one large partition.

I do like having Ubuntu (for emergency boot) on every drive.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

And now I prefer gpt if not installing Windows as it has a few advantages. But then if drive may ever get moved to a new UEFI system, I want an efi partition at beginning of drive for UEFI boot and a bios_grub partition for BIOS boot. Neither are large, so not much of drive is not used for data. If later you want an efi partition it can be difficult to add when drive has lots of data.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

These instructions are for moving /home from inside / (root) to a new partition. But your copy and remount with new UUID in fstab should really be the same.
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

