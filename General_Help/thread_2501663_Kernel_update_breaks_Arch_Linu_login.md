---
title: "Kernel update breaks Arch Linu login"
date: 2024-10-16
forum: General Help
---

### Post by rabiluria on 2024-10-16
Hol, greetings, I am new to this for, I have installed on my Thinkpad T480 lenovo Ubuntu 24. 10, Arch Linux and Windows 10, my concern is the following, when Ubuntu was updated, in one part of the process, did update grub and all that follows, and the consequence is that It renamed the Arch folders, @home, and all the others I put them @ and that way I could not enter Arch and it was necessary to install it again, my concern is 1) is it possible that only update the grub and the kernel without making undate grub, and all the process that accompanies it, or someone has happened that way to rename the folders and how to solve it.
Thank you for your kindness.
Cordially rabiluria

---

### Post by grahammechanical on 2024-10-16
I will explain. This applies to all distributions of Linux. Whenever there is an update/upgrade to a newer Linux kernel the boot loader has to also be updated otherwise it will not load into the newer Linux kernel.

Ubuntu uses the Grub boot loader. Every time that a new Linux kernel is installed the Grub boot menu files are reconfigured to put the new Linux kernel at the top of the list of kernels to boot. This reconfiguration process will also search for other boot loaders that are on any drives attached to the machine.

If we are dual booting more than one distribution of Linux we should decide on a distribution to be in control of the Grub boot menu. When the other distributions get an updated Linux kernel we should boot into the distribution in control of the boot menu and run

[code]sudo update-grub]

Then the boot menu will offer an option to boot into the new kernel on the other distribution.

As for folders with this symbol @ as part of the folder name, I think that this is happening because the installation is running on a BTRFS file system.  Is this true? If I remember correctly, with BTRFS it is possible to take snapshots of the installation before serious upgrades to the operating system. Then if the upgrade breaks something the user can revert to the version of the operating system that was being used before the system update/upgrade.

Are you using BTRFS? Have you setup Arch Linux to use BTRFS?

This is old documentation but it does prove the use of @ symbol

> Subvolumes are created below the top of the btrfs tree as needed, e.g. for **/** and **/home**, it creates subvolumes named **@** and **@home**. This means that specific options are needed in order to mount the subvolumes, instead of the default btrfs tree top: 

[LIST]
[*]The **@** subvolume is mounted to **/** using the kernel boot option *rootflags=subvol=@* 
[*]The **@home** subvolume (if it is used), is mounted via the mount option *subvol=@home* in fstab. 
[/LIST]
  
[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Regards

---

### Post by rabiluria on 2024-10-16
Thank you for your reply, indeed both operating systems are running btrfs.

---

### Post by rabiluria on 2024-10-16
Does that mean that what I see when I open the partition are snapshopts?

---

### Post by grahammechanical on 2024-10-16
It has been years since I last experimented with BTRFS on Ubuntu. What you are seeing is standard for a BTRFS file system. I think that is correct. It separates the operating system (we call it root. it is symbolised as /) and the user data (called home). It means the user can make a snapshot of the root folder and not the home folder. Or, the home folder and not the root folder. Or both if that is what the user chooses to do.

You most likely will need to install apt-btrfs-snapshots if you want to take snapshots and delete them. I cannot help you much because so much time has passed since I last used a BTRFS file system.

[https://moritzmolch.com/blog/2506.html](https://moritzmolch.com/blog/2506.html)

I would be nice if there existed a utility with a graphical user interface to make managing BTRFS snapshots. I do not know of one.

Regards

---

