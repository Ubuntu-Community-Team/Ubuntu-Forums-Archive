---
title: "Installation of ubuntu studio alongside Linux mint?"
date: 2023-05-19
forum: General Help
---

### Post by isprins on 2023-05-19
Hi, is it possible to install ubuntu studio alongside Linux mint, without messing up the grubs boot order?

---

### Post by ajgreeny on 2023-05-19
The quick and simple answer to your question is "No" but that is not the total answer.
Normally the OS installed last, ie Ubuntu installed alongside the Mint that was already installed, would take over the management of grub on the computer and would place Ubuntu at the top of the grub menu.

Following that second installation it is possible to ensure that Mint is still the default OS booted from grub by editing the /etc/default/grub file to change the **GRUB_DEFAULT=0** line to another number which points to Mint instead, probably **GRUB_DEFAULT=2.**

You can I think  also boot to Mint from your new Ubuntu grub menu and when running Mint use command ***sudo grub-install /dev/sda*** assuming that /dev/sda is the drive you have; edit that if needed to point to the correct disk. Then run ***sudo update-grub*** to make sure all is OK.

---

### Post by guiverc on 2023-05-19
Depending on release & details you've not provided, yes it maybe possible, but in my opinion it's not worth even trying.

I have a PC that I consider my *secondary* PC that I use ~2+ hours per day; its a multi-OS system and my preferred OS on that box is the Debian system I've setup for myself. Less than 2 days ago I performed a Lubuntu *jammy *(22.04) *daily* install on it as a *regular* QA-test install which I do ~weekly. After that install (*a non-destructive install*) I check out each of the installed OSes was *untouched* & operate as they did before (*skipping Debian*), then test out the newly (*re-*)installed Lubuntu *jammy* ensuring my data there wasn't erased, my music playlists continued using my non-standard music player etc.. (*the purpose of the install*) then my final step is to boot into the only OS that I'd not tested to that point which is the Debian install I care most about. Once I've confirmed Debian is all okay; I just `grub-install` and have it take ownership of the boot process back & the box is back as if the install never happened.

I used to *play* and *fight* with installers & have `ubiquity` not-write a bootloader & thus know it's possible (note: I've not tried to do this `calamares` as I'd decided it wasn't worth it; Ubuntu Studio has used `calamares` for recent release & you didn't specify release); but it's just not worth it & risks doing damage. The best approach in my opinion (*and I'm doing this ~80 times per year* *on systems I value*) is just perform the install, then correct/change it to what you actually want.

FYI:  I used to write the ISO to installation media in specific ways that `ubiquity` would always [*attempt to*] write the bootloader to the USB installation media instead of my actual HDD/SSD, it'd fail & no boot loader was written (ie. *I'd accomplished what I wanted.. how you write the ISO to do this varies on your hardware though*!)  It's just not worth it & I decided that approach was too risky given things keep changing..

---

### Post by yancek on 2023-05-20
It is possible  but the determining factors are your experience in doing so.  In addition to the information posted above, if you have an EFI system and install in EFI mode, the second install (Ubuntu Studio) will overwrite the boot files on the EFI partition which are in a directory named ubuntu.  Many Ubuntu distributions do this (use ubuntu as the EFI directory).  This can be corrected easily by running the blkid command and determining the partition on which Mint resides and replacing the UUID entry in the grub.cfg file on your EFI partition with the UUID entry for the Mint partition.

In the past, users were usually given the option during install to select to install the boot loader to the system partition rather than the MBR or EFI partition.  If you use the manual (Something Else) option, you may be able to use that.  It is very difficult to install to a partition after the initial installation.

---

