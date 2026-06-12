---
title: "NTFS  ==&gt; fuseblk"
date: 2007-06-03
forum: General Help
---

### Post by moonhost on 2007-06-03
hi, I installed Ubuntu 7 yesterday (dual system: Win XP & Ubuntu 7) . Everything went smoothly. And the partition for windows XP (NTFS) can mount automatically on the desktop when I boot Ubuntu, though I can only read. Today I added NTFS Configuration Tool (NTFS-3G) :

*_[COLOR="Blue"]sudo apt-get install ntfs-3g ntfs-config[/COLOR]_*

so that I have read/write access to the NTFS partition. After the installation,  I rebooted, but the NTFS partition could not mount automatically.  [COLOR="Red"]***How can I make the NTFS partition mount automatically  again at each reboot? ***[/COLOR]

*[COLOR="Blue"]~$ sudo fdisk -l[/COLOR]*

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3919    31472248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           11568       12161     4770360   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            3920        4810     7156957+  83  Linux
/dev/sda4            4811       11567    54275602+   5  Extended
/dev/sda5            4811        7360    20482843+  83  Linux
/dev/sda6            7361        9272    15358108+  83  Linux
/dev/sda7            9273       11057    14337981   83  Linux
/dev/sda8           11058       11567     4096543+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by shirilover on 2007-06-03
Go to: Applications->System Tools->NTFS Configurtation Tool
enter your password at the prompt
check the appropriate boxes to enable write support
Click OK.

This should work so long as your windows drive is listed in /etc/fstab

---

### Post by moonhost on 2007-06-03
> **shirilover said:**
> Go to: Applications->System Tools->NTFS Configurtation Tool
enter your password at the prompt
check the appropriate boxes to enable write support
Click OK.

This should work so long as your windows drive is listed in /etc/fstab

I already did that before I posted the thread.  [COLOR="Red"]Selected[/COLOR] Enable write support for **[COLOR="Red"]both[COLOR="Green"] internal[/COLOR] and [COLOR="Green"]external[/COLOR] [/COLOR]**device.

The partition for Windows XP is changed [COLOR="Red"][COLOR="Blue"]*NTFS==> fuseblk*[/COLOR][/COLOR], and it is in
**[COLOR="Blue"]/media/sda1[/COLOR]**.

---

### Post by szaka on 2007-06-04
> **moonhost said:**
> 
The partition for Windows XP is changed [COLOR="Red"][COLOR="Blue"]*NTFS==> fuseblk*[/COLOR][/COLOR], and it is in
**[COLOR="Blue"]/media/sda1[/COLOR]**.
That's the expected, your NTFS is mounted fine read-write. If you can't access it then you probably have permission problems, maybe only root or certain users can access it.

---

