---
title: "Problems with mounting permissions"
date: 2018-10-30
forum: General Help
---

### Post by martasanz34 on 2018-10-30
Hi,
 I have a laptop with a dual system installed, running windows and ubuntu 18.04.
 
I have a 128gb SSD where I have the system partition with the EFI system, a microsoft reserved partition, the windows OS partition and a recovery partition. I also have a 1 Tb HDD With a Data partition in NTFS,  a swap partition and an Ext4 partition, where the mounting point is installed.

Today I realized I could't write any file in the Data partition, so I used the Disks utilities and following a tutorial I tried to change mounting options. The problem is that I messed up and instead of the Data partition I somehow modified the System partition permissions instead (/dev/sda1 Efi system).
After rebooting I can access the grub, but if I choose linux I get to a terminal-like screen saying I'm in emergency mode and I should push enter for maintenance or Ctrl+D to continue. If I push Ctrl+D I get " Unrecognised mount option "umask=000 0 0”( the parameters I input in the Disks program by mistake) or missing value. Can't access linux".

I tried pushing enter, and doing a nano /etc/fstab to remove the "umask=000 0 0", but it's not written there. Any ideas of what I can do? 

I tried to access the disk program from the live CD and change the mounting permissions back to normal, but it didn't work.

Windows starts normally.

---

### Post by martasanz34 on 2018-10-30
Solved: I mounted the partition automatically and then pushed control+D to reboot. I could access the desktop and modify the mounting permissions with the disk utility.
Thanks

---

