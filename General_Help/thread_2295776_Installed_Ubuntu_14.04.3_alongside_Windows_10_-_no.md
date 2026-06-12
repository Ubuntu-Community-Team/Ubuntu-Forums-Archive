---
title: "Installed Ubuntu 14.04.3 alongside Windows 10 - now windows doesn't boot"
date: 2015-09-21
forum: General Help
---

### Post by allonnissos2 on 2015-09-21
I have a Fujitsu Lifebook A series which had Windows 1 installed. I installed Ubuntu 14.04.3 LTS alongside it, but now it will only boot to Ubuntu (but I can see the windows partitions appear to be still there).

Method:

With Windows 10 installed I inserted a DVD with the Ubuntu 14.04.3 iso on it. On rebooting I chose the option: Install Ubuntu.
On the next screen I chose "Install Ubuntu alongside Windows 10"
I chose to partition the 1Tb HDD into 524Gb for Windows 10 and 454Gb for Ubuntu.

All went well and Ubuntu installed correctly.

I then rebooted and get the grub loader with the following options:

Ubuntu
Advanced options for Ubuntu
Windows Boot Manager (on /dev/sda2)
System Setup

If I choose Ubuntu - it loads the login page and I can log in normally
If I choose the Windows Boot Manager I get the following message:

/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/Sata(0,0,0)/HD(2,96800,31800,b4178dcd35326249,2,2)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image

Press any key to continue...

From within Ubuntu I can see the files within the Windows partition so I am assuming it is all there, and only the boot loader is corrupt?

Any assistance welcome.

---

### Post by oldfred on 2015-09-21
Did you leave Windows always on hibernation or fast start up on? That must be off to dual boot.
If UEFI, you should be able to directly boot into Windows from UEFI boot tab.
If BIOS you may have to temporarily reinstall Windows boot loader to MBR.

Best to see details so we can make better suggestions:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by allonnissos2 on 2015-09-21
Thanks. Issue is resolved. The problem was that "Secure Boot" in the bios was screwing it up. Having disabled it, it now works as I would expect it to. Thanks for the assistance. Thread can be closed

---

