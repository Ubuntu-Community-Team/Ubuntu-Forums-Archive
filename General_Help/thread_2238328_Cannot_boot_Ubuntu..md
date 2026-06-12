---
title: "Cannot boot Ubuntu."
date: 2014-08-07
forum: General Help
---

### Post by henry27 on 2014-08-07
So yeah, I fully installed the lastest version of ubuntu onto my 2tb removable drive. But I cannot see the 2tb drive in bios, hence i cannot boot into that drive.
I can see the boot option for ubuntu on my 16gb usb stick (it was made into bootable usb using unet something), but not the 2tb one.

I have tried boot-repair recommented repair on the ubuntu from 16gb usb stick, it messed up my windows 8 boot. Now I get 0xc0000428 error and cannot verify the digital signature of system32/winload.ext file at boot. And I still cannot see the 2tb drive in bios.


What can I do to see ubuntu boot option and boot into windows 8?

pls help. Im dying T_T Pls pls pls pls pls pls pls

---

### Post by yancek on 2014-08-07
If the BIOS does not recognize the 1TB drive then you won't be able to boot or access anything on that drive.  How did you manage to install Ubuntu to that drive if it was not recognized in the BIOS?  Which version of windows do you have on this computer?

---

### Post by henry27 on 2014-08-07
Yes. Bios cannot detect my drive. My drive is seagate 2tb. So I cannot boot into ubuntu on that drive.
However my ubuntu and windows 8 does detect seagate 2tb after booted. Thats how I installed ubuntu onto that drive.
I can still access the files in my 2tb drive in the usb-booted ubunted.

The main problem is how can I start up windows 8? Cos I cannot do anything in in usb ubuntu, it cannot save the settings and programme installed, so I have to reset them everytime i reboot.
If I can start up windows8, then I can move onto the bios not detecting 2tb drive problem.

---

### Post by henry27 on 2014-08-07
Will downgrade windows 8 to 7 solve the "cannot verify the digital signiture of winload.exe" problem?

---

### Post by oldfred on 2014-08-07
Windows 7 installed in BIOS mode creates even more issues. But if you install in UEFI mode it may be ok.
Windows 8 does have lots of issues. fast boot(always on hibernation), secure boot, resetting itself to first in UEFI and others.

Did you turn fast boot or always on hibernation off. To dual boot that must be off.
Also generally better but not required to turn secure boot off.
Currently you cannot boot Windows from grub menu with secure boot on..

When you ran Boot-Repair did you run its 'buggy' UEFI fix? If so undo that.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

And post link from BootInfo report it creates, so we can see details.

Did you boot flash drive in UEFI mode and install to external drive in UEFI mode?
Install to a second drive requires a bit more detail, including making sure you have an efi partition on external and not use efi partition on internal drive.

This is a flash drive, but could be any external drive.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

If installing to any second drive ignore issues on shrinking Windows. But good backups with any system change are required.
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

