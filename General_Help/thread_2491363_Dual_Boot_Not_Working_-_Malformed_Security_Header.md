---
title: "Dual Boot Not Working - Malformed Security Header"
date: 2023-10-05
forum: General Help
---

### Post by tdkhan on 2023-10-05
I have been using Ubuntu alongside windows 11 for more than a year without any issue. Yesterday when I ran my system I got the following errors

Malformed Security Header
Failed to read header: Invalid Parameter
Failed to load image: Invalid Parameter
start_image() returned Invalid Parameter, falling back to default loader
Malformed Security Header
Failed to read header: Invalid Parameter
Failed to load image: Invalid Parameter
start_image() returned Invalid Parameter

and it then runs windows 11.

Looking at online forums I saw that disabling secure boot might help so I tried it but to no avail. 

I then created a Ubuntu-live USB, and tried using the boot-repair tool but it continues to run an in an infinite loop for hours displaying the following message

Applying changes. This may require several minutes..

I tried the boot repair tool with and without the secure boot  but nothing works. Here is the link to the boot info file from the boot repair tool

[https://paste.ubuntu.com/p/ZtzPQYzx6d/](https://paste.ubuntu.com/p/ZtzPQYzx6d/)

I use Ubuntu primarily for ROS and am not very savvy about the operating system itself. I would appreciate any help in fixing the issue.

PS. I do not recall any windows update that happened before I ran into the issue, I do recall doing an update and upgrade on the ubuntu system before I switched to the windows to do some tasks.

---

### Post by Rubi1200 on 2023-10-05
You can boot into Windows 11 normally?

I would first try turning off Bitlocker, if enabled, and then see if you can access Ubuntu.

---

### Post by samxamnam on 2023-10-12
Hey, I experienced the exact same problem today. On a 23.4 Ubuntu with Windows 11 as dual boot.

I used this answer [1] to reinstall Grub using an old usb-stick with Ubuntu 20.4 (I even forgot the update-grub command). Anyway, after a reboot, everything worked again.

Hopefully this helps.


[1] ([https://askubuntu.com/a/831241](https://askubuntu.com/a/831241))

---

### Post by vishalvivekm on 2023-10-18
Hi, thanks!
I'm facing the same situation.
I did look up the solution you referred to [https://askubuntu.com/a/831241](https://askubuntu.com/a/831241)

I, however, wasn't able to understand what does sdX, sdXX, sdXY mean.
>  [COLOR=#232629][FONT=-apple-system]Note : [/FONT][/COLOR]sdX[COLOR=#232629][FONT=-apple-system] = disk | [/FONT][/COLOR]sdXX[COLOR=#232629][FONT=-apple-system] = efi partition | [/FONT][/COLOR]sdXY[COLOR=#232629][FONT=-apple-system] = system partition

could you please help how exactly you did it?[/FONT][/COLOR]

---

### Post by oldfred on 2023-10-18
@tdkhan
If you look at list of boot order line 87, you will see the first entries are all you USB drives. And they looks like VenMsg type entries.
Those often are from disconnected drives. You should use efibootmgr with -b parameter to remove those and move Windows or Ubuntu which every you boot mode to first in boot order with efibootmgr and -o parameter. See
man efibootmgr

Drives are sda, sdb, sdc etc for SATA types. Some now are NVMe drives like nvme0n1, nvme1n1 etc.
Then partitions are the number at end or sda1 is first partition on sda drive.
You can see drive & then number of partion from live installer with 
sudo parted -l
sudo fdisk -lu

---

