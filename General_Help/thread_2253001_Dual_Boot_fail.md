---
title: "Dual Boot fail"
date: 2014-11-16
forum: General Help
---

### Post by Prasanna.T.R. on 2014-11-16
I tried installing ubuntu 14.10 alongside windows 8.1. I thought since the new option to install alongside windows was available, i needn't fix boot things... but when it restarted into 8.1 , i used usb to try ubuntu, then tried the boot-repair procedure. It gave me this error after all things were going smooth.

[http://paste.ubuntu.com/9046233/](http://paste.ubuntu.com/9046233/)

Can anyone please read this and tell me what im doing wrong?Im installing this on a hp laptop with UEFI bios.Secure boot is turned off, so is fastboot.

---

### Post by ajgreeny on 2014-11-16
But did you follow everything mentioned in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) including booting the install medium (DVD or USB) in the mode in which Ubuntu is needed, ie UEFI mode.

---

### Post by oldfred on 2014-11-16
HP and others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.
      
 script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

---

