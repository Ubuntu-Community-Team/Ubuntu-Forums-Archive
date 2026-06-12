---
title: "Ubuntu on Mac, Boot issue etc."
date: 2019-09-07
forum: General Help
---

### Post by judasviking on 2019-09-07
Hey guys!

I have boot issues, no EFI file and i tapped continue under the installation.

I have got a little guide how to make this work by creating a new partition with ext4 and i did.

Right now im stuck where im gonna edit the fstab file and where/how to find it?

I installed the ext4 on dev/sda2 and fat32 on sda3.

Please help me since im afraid of turning of my mac now.

I really appricete a good explanation and steps since im quite new to linux, thanks guys!

---

### Post by judasviking on 2019-09-07
So i basicly got this guide, but im stuck at stage 9.

 You can create an ESP after installation if the installer did not make one:
  
[LIST=1]
[*]Get your Ubuntu installation media, and boot it. Chose the option to *Try Ubuntu without installing* (because we will **not** be re-installing Ubuntu).
[*]When the Ubuntu live has booted, go to the applications list, and find and launch **Gparted**.
[*]Inside Gparted, find the disk on which Ubuntu is installed on and select it from the dropdown at the top.
[*]You should see an ext4 partition on this disk (and possibly a swap partition as well). Resize the ext4 partition so that there is 500MB of unallocated space afterwards. In this space, make a FAT32 partition.
[*]Now assign the esp flag to the partition.
[*]Apply all the operations to confirm the changes.
[*]Now take note of the partition name (eg: /dev/sda2).
[*]Now you need to edit a file on the ext4 partition (mount it if it not already mounted (may require rebooting the installation media)).
[*]In **Files**, go to /media/ubuntu/LABEL_OF_EXT4_PARTITION/etc/fstab (label will be different to name (might even be a hash)). Edit the fstab file with the text editor.
[*]Add a line to the end of the file with the following line: /dev/sdxy   /boot/efi    fat32    defaults    0 2, where x and y refer to the partition name (such as a2 in /dev/sda2).
[*]Save and close.
[*]Finally, ensure the mountpoint exists. Go to /media/ubuntu/NAME_OF_EXT4_PARTITION/boot and look for a folder named efi. If one does not exist, create one.
[/LIST]
  This should give you a working ESP for Ubuntu. You should now be good to reboot normally.

---

