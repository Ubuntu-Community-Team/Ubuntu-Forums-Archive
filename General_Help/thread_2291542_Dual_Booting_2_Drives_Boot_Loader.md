---
title: "Dual Booting 2 Drives Boot Loader"
date: 2015-08-20
forum: General Help
---

### Post by xcurtisx on 2015-08-20
Good Day.
I thought I would give dual booting my system tonight.
I had a spare drive and installed Ubuntu there.
However I am not getting prompted at boot to choose that as an option.
I am booting straight into Windows 10 like nothing happened.
I swapped boot devices in bios and the Ubuntu system boots fine.
How do I get the boot option on my main disk and not lose the data on my main disk / my windows 10 install?
Thanks!

---

### Post by yancek on 2015-08-20
The methods are different depending upon whether you have windows 10 and/or Ubuntu installed using UEFI or MBR.  You can check this by getting into the BIOS setup on boot and looking at the various options.  You can also check your partitions from Ubuntu to see if you have an EFI partition. When you determine which method you are using, post back and someone should be able to help you.

---

### Post by oldfred on 2015-08-21
With two drives & two installs often a good idea to run the Summary report just to know what is really where and how system is configured.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by xcurtisx on 2015-08-21
Took a few pics - will boot back into linux shortly to get the Boot Info file requested as well.
Thanks!
Windows is on my 128 and Linux on my 500.
The 1tb is just storage



[IMG]http://s30.postimg.org/no2y25aap/IMG_20150821_240313530.jpg[/IMG]

[IMG]http://s30.postimg.org/ryhlxqfdt/IMG_20150821_240336223.jpg[/IMG]

---

### Post by oldfred on 2015-08-21
Please attach screen shots, not post in line.
You can use paperclip icon in Forum's Advanced editor.

Normally drives should be AHCI, not IDE.
And I have had issue of flash drives becoming different device (/dev/sda) depending on whether plugged in when booted or rebooting with it plugged in, when I skipped a SATA port. My normal sdb drive would then be sdc and sdb became flash drive as I had skipped the second SATA port.
I also had similar issue in UEFI where UEFI/grub saw second drive as hd2 (hd0 is first, hd1 is second), but it was sdb. It turned out I had DVD in middle of drives. 
Or just better to use SATA ports in order.

---

