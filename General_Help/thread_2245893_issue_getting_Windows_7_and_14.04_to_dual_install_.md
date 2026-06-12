---
title: "issue getting Windows 7 and 14.04 to dual install properly"
date: 2014-09-26
forum: General Help
---

### Post by eival on 2014-09-26
i tried installing windows first, but 14.04 didnt see the windows partition (which is only 100gigs of 1 tb)

i tried reformating the empty partition but Ubuntu still didnt see it.

now im reinstalling W7 for the full HDD and hoping ubuntu will then offer to resize that and install next to it

if that doesnt work, what else can i try?

im mainly getting the GMT filesystem error, which is why i couldnt install W7 behind U14 in the first place

---

### Post by oldfred on 2014-09-26
You mean gpt partition error?

If system was UEFI with gpt partitioning and you install a different copy of Windows in BIOS mode it converts to MBR partitioning, but does it incorrectly. You can install Windows 7 in UEFI mode if you copy to flash drive an do some updates.

But if drive is now MBR with the gpt error you can run fixparts to remove the backup partition table that Windows left.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by eival on 2014-09-27
yeah the computer im trying it on has UEFI, finally got fed up and just put U14 back on it, except now my BIOS still shows 2 versions of ubuntu under the UEFI menu.

would reformating the entire drive with a GPARTED live usb fix that?

---

### Post by oldfred on 2014-09-27
UEFI often shows two versions of ubuntu as one is a link to shim for secure boot and the other is to grub for standard UEFI boot.

I would leave them, but if you want to delete:
 # from liveDVD or flash and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

