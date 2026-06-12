---
title: "New Laptop"
date: 2013-03-01
forum: General Help
---

### Post by jimmac49 on 2013-03-01
As the title says I recently had to buy a new laptop, unfortunitely I did net read the specs, and I have ended up with a Windows 8 laptop,
as of today I have had no joy in removing the said OS.
I need to get rid of windows and install 12.04, is there any way to do this I have googled and tried suggestions but to no avail.

As always all help, Ideas and suggestions greatly appreciated.

Jim

---

### Post by oldfred on 2013-03-01
What laptop. Some install Ubuntu easily, some with difficulty and some not at all. And a few become bricks with any Linux install.
Also is it an UltraBook with Intel SRT? That adds complications.

Best to dual boot until all the UEFI issues by Vendor on UEFI design, Windows and Linux are resolved.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop

[/URL] Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
      
 Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)

     
[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]
[/URL]

---

