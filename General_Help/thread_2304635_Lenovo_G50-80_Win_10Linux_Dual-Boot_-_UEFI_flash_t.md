---
title: "Lenovo G50-80 Win 10/Linux Dual-Boot - UEFI flash to original? Remove ubuntu entry?"
date: 2015-11-28
forum: General Help
---

### Post by ron45 on 2015-11-28
As stated in the subject line, I am on a Lenovo G50-80 laptop w/  Windows 10 x64. I have recently been experimenting with a couple Linux  OSs in a dual boot configuration with complete success. I have though  since decided to dedicate another machine to my Linux ambitions.
 
My  partition is expanded back to norm, all is well with that, however, it  still has ubuntu listed in the boot menu and I have been unable to  remove it as it keeps being "reinstalled" w/ another {identifier} in  BCDedit.
 
Is anyone aware of how I can delete the  identifier and have it not return (it's obviously stored elswhere) or  simply reflash the BIOS to it's original state?
 
NOTE: in BCDedit, /fixmbr or /fixboot had no effect. Also the most recent available update to the UEFI had no effect either.
 
This  is really a non-issue as far as the functionality of the laptop goes,  it's more of myself wanting the answer and satisfying that OCD side of  myself.......lol.
 
Any help would be appreciated.

---

### Post by QDR06VV9 on 2015-11-28
When you boot to windows go to the start menu 
Type MSCONFIG into the Start/search box. Then hit Enter. Go to the BOOT tab and remove it there.[B]
EDIT: The Only other method that I know to work is this
[/B]Visual BCD Editor
[http://www.boyans.net/DownloadVisualBCD.html](http://www.boyans.net/DownloadVisualBCD.html)

And of course the be careful with what you are removing.
Screenshot Attched
Regards

---

### Post by oldfred on 2015-11-29
Check your ESP - efi system partition. You need to remove /EFI/ubuntu. Some UEFI keep adding entries found in the ESP to the UEFI boot.
Then you need to use UEFI or efibootmgr from live installer in UEFI boot mode to remove UEFI entries.
I believe BCD syncs with entries in UEFI, not not sure if deletion from BCD works or not.

       Check entry is there.
sudo efibootmgr -v 

 Delete entry change XXXX to entry you do not want:
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

Some UEFI require all 4 hex char (leading zeros), others just the one or two significant ones.

---

### Post by ron45 on 2015-12-15
The following link was my answer. Thanks everyone!

[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

---

