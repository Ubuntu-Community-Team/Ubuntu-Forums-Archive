---
title: "Making a primary partition bootable"
date: 2013-11-08
forum: General Help
---

### Post by vaditya04 on 2013-11-08
I used testdisk to recover my partitions after a long list of poor decisions and mishaps.
  
Now when I rebuilt my partitions, I was unable to select one of the  partitions as bootable (*). I was forced to choose all my partitions as  Primary (P). Now I have a windows partition which I want to make  bootable.

  
I played around in the Windows command prompt with my limited  knowledge and tried to make the windows os partition active. The error  returned was "not a fixed mbr partition" or something like that.


  What should I do? Should I try to deep search with testdisk again or  try something with Gparted. I want to avoid the former option because it  takes hours to finish a deep search.

  Thanks very much.

---

### Post by jamesisin on 2013-11-08
What exactly is your configuration?  Is it a dual boot with Windows 7 and Ubuntu 13.10?

---

### Post by oldfred on 2013-11-08
I did not think there were any limits with gparted or testdisk on setting boot flag. Windows only  allows boot flags on primary partitions, but the old Lilo boot loader uses boot flag even on logical partitions. Grub does not use boot flag.

Post this. You may still have some sort of partition table issue.
       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

---

