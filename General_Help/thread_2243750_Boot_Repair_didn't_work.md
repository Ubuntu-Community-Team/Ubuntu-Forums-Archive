---
title: "Boot Repair didn't work"
date: 2014-09-10
forum: General Help
---

### Post by sean61 on 2014-09-10
So I booted windows 8.1 and now I can't run Ubuntu. Heres my url: [http://paste.ubuntu.com/8314770/](http://paste.ubuntu.com/8314770/)

---

### Post by yancek on 2014-09-10
The output you posted shows several windows ntfs/vfat partitions.  The only Linux partition seen is a swap partition on sda4.  In the section Drive Partition info, sda4 shows as Microsoft Reserved partition.  There is no partition with any Linux system on it and there are no Linux boot files. The sda5 partition shows as unknown filesystem.   The only boot files are on the flash drive.  If you want Ubuntu, you will need to reinstall it and since windows uses GPT/EFI, make sure you select that option when installing Ubuntu.

---

### Post by oldfred on 2014-09-11
Was sda5 your Linux file system?
It may just be corrupted, but as yancek suggests you may need to reinstall. 
But do not use any of the auto install options, they will erase entire system. Only use Something else and choose sda5 as / (root) to reformat as ext4. It will auto find swap and reinstall ok.

You could try running fsck from live installer.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

    
You show Windows is still hibernated. You must turn off fast boot or always on hibernation if dual booting. Even dual booting two Windows as it will lead to issues.

---

