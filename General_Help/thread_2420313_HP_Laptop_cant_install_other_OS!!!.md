---
title: "HP Laptop cant install other OS!!!"
date: 2019-06-03
forum: General Help
---

### Post by wayi on 2019-06-03
[COLOR=#000000]Ok so my HP Laptop (HP Pavillion Sleekbook) Came with Windows 8. I installed Ubuntu and my retarded self let it overwrite all my partitions. Now whenever i boot into recovery mode, it just boots into ubuntu. Ive tried putting windows 10 on a bootable usb, but it gets 99% moving the iso and then i get an error. ive also tried putting windows 10 on my usb from the Startup Disk Creator. also an error. Any ideas? I just want windows or OSX back.[/COLOR]

---

### Post by Autodave on 2019-06-03
Windows will have to be installed first, and then 'buntu.

---

### Post by crip720 on 2019-06-03
One of maybe two problems.  Putting a Windows ISO on a USB from ubuntu is not straight forward, might need 'woeUSB' or something similar.  Two, you might need to have a 'NTFS' partition on laptop for Windows to install on.  Can use gparted on a bootable live ubuntu USB to make a NTFS partition/disc on the laptop.

---

### Post by oldfred on 2019-06-03
UEFI or BIOS.
If system was Windows 8, it is UEFI, but you may have installed Ubuntu in either UEFI or BIOS boot mode.
Windows only boots in BIOS mode from MBR partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.

If UEFI, you can install Windows after Ubuntu, but need unallocated space.

If BIOS/MBR, Windows only installs to unallocated space with available primary partition or NTFS primary partition with boot flag. But Windows has a "feature" in BIOS installs & upgrades where it deletes any logical partition table entries for Linux partitions. Partition still exists, but just not in partition table. Back up data & separately backup partition table or know start & end in sectors of every partition, so repairs can be easily made.

How you boot install media UEFI or BIOS for both Ubuntu & Windows is then how it installs. If on one drive, both must be in same boot mode. If separate drives, still better if both are in same boot mode, and some issues if both drives seen during install.

If UEFI hardware which all systems since Windows 8 released, better to have both systems installed in UEFI boot mode on gpt partitioned drive.

Be sure to have good backups.

---

### Post by HermanAB on 2019-06-03
Install Virtualbox or Gnome Boxes, create a virtual machine and install Windows in that.  

Then, you can run Windows in a window, the way the computer gods intended.

---

