---
title: "installed ubuntu to /dev/sdb and then that drive became /dev/sda and I cant boot"
date: 2019-01-21
forum: General Help
---

### Post by Macmee on 2019-01-21
I installed windows and ubuntu to a ssd connected by USB (sdb) and then later inserted it into the machine with SATA (so it became sda). Now I can't boot Ubuntu.

specifically: I had an internal hard drive at /dev/sda with nothing on it. I had an ssd at /dev/sdb:

/dev/sdb1 was EFI /dev/sdb2 was windows /dev/sdb3 was ubuntu

I opened the computer to ditch the hard drive at /dev/sda and I put the SSD in instead which is how it became /dev/sda. So now my reality is:

/dev/sda1 was EFI /dev/sda2 was windows /dev/sda3 was ubuntu

I thought "no problem" and just booted from the live disk, and I deleted and re-created the entry for windows using efibootmgr and windows now boots fine. But when I did efibootmgr -v I saw that the ubuntu entry didn't point to an efi file, but just showed up with some big uuid looking thing. Whereas window's entry looked like:

**windows 10 (GPT, 1, \efi\boot\bootx64.efi)**

the entry for ubuntu was just:

**ubuntu (134fde-234f3....)**

so I don't know how to fix it because I can delete it no problem, but when I create a new record I don't know where to point the location to the efi file to. I mounted my efi partition and poked around and I actually couldn't even find anything related to grub.

So... my questions are:

    What can I do to fix my efi setup here to boot into ubuntu again after moving the drive from being sdb to sda, and

    Why does Window's entry in the EFI table point to an efi file, but Ubuntu's points to a UUID? How does that work and why does the EFI partition seemingly contain no efi file for grub at all?

---

### Post by ajgreeny on 2019-01-21
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2019-01-21
Best next step is to take the advice and use boot repair with the Create BootInfo Script option and do NOT try to make any repairs.  Simply post the link you get when boot repair finishes here.

Using the Ubuntu Live install usb, when you mount the EFI partition (sda1) do you see an ubuntu directory with files in it?  If not, you installed incorrectly and in all likelihood have a Legacy install.  Posting the boot repair link will give that info if that is the case.

Did you read the official Ubuntu documentation on dual booting UEFI with windows 10 at the link below?  The site explains the process in detail.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Macmee on 2019-01-21
> **ajgreeny said:**
> See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

> **yancek said:**
> Best next step is to take the advice and use boot repair with the Create BootInfo Script option and do NOT try to make any repairs.  Simply post the link you get when boot repair finishes here.

Using the Ubuntu Live install usb, when you mount the EFI partition (sda1) do you see an ubuntu directory with files in it?  If not, you installed incorrectly and in all likelihood have a Legacy install.  Posting the boot repair link will give that info if that is the case.

Did you read the official Ubuntu documentation on dual booting UEFI with windows 10 at the link below?  The site explains the process in detail.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)



here's the output from boot-repair:

[https://paste.ubuntu.com/p/SCCNrPTvbR/](https://paste.ubuntu.com/p/SCCNrPTvbR/)

And no I never read the dual booting windows 10 guide. Back when my SSD was at /dev/sdb I just made a ext4 partition, installed ubuntu onto it and used efibootmgr to re-insert a record for \efi\boot\bootx64.efi and that allowed me to dual boot until I moved the drive to /dev/sda

---

### Post by oldfred on 2019-01-22
When you unplug a drive, UEFI normally forgets entry. Many UEFI often find Windows, but not Ubuntu entry in UEFI.
So you just need to reset UEFI entry for Ubuntu with efibootmgr.

Also Windows normally boots /EFI/Microsoft/Boot/bootmgfw.efi.
And /EFI/Boot/bootx64.efi is a hard drive or fallback boot entry.
Boot-Repair will normally copy bootx64.efi and make a backup, and then make bootx64.efi as a copy to shimx64.efi to boot Ubuntu. It then may add an UEFI entry to boot the backup bkpbootx64.efi.

Try running the fixes suggested with Boot-Repair.

For more info on efibootmfg see
man efibootmgr

Examples of use of efibootmgr also in link in my signature.
I posted the same entries here, but someone else renumbered, I assume the English preferred title & sub-title format which I forgot long time ago.
[https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by Macmee on 2019-01-22
> **oldfred said:**
> When you unplug a drive, UEFI normally forgets entry. Many UEFI often find Windows, but not Ubuntu entry in UEFI.
So you just need to reset UEFI entry for Ubuntu with efibootmgr.

Also Windows normally boots /EFI/Microsoft/Boot/bootmgfw.efi.
And /EFI/Boot/bootx64.efi is a hard drive or fallback boot entry.
Boot-Repair will normally copy bootx64.efi and make a backup, and then make bootx64.efi as a copy to shimx64.efi to boot Ubuntu. It then may add an UEFI entry to boot the backup bkpbootx64.efi.

Try running the fixes suggested with Boot-Repair.

For more info on efibootmfg see
man efibootmgr

Examples of use of efibootmgr also in link in my signature.
I posted the same entries here, but someone else renumbered, I assume the English preferred title & sub-title format which I forgot long time ago.
[https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Thank you! I got back into grub and ubuntu! Using grub I can also boot windows since grub finds bootmgfw.efi, but just like you said boot-repair moved bootx64.efi around. I manually put it back and used efibootmgr to create an entry for windows again but upon rebooting and trying to select it, my system just restarts. I tried creating an entry for booth bootx64.efi as well as /efi/microsoft/boot/bootmgfw.efi. After booting back into ubuntu and running efibootmgr -v I see this for windows:

Boot0000  Windows 10	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

and my fdisk output:

Device         Start       End   Sectors   Size Type
/dev/sda1         40    409639    409600   200M EFI System
/dev/sda2     411648 479827967 479416320 228.6G Microsoft basic data
/dev/sda3  479827968 976771071 496943104   237G Linux filesystem

the command I used to create the w10 entry:

sudo efibootmgr --create --disk /dev/sda --part 2 --loader "\efi\boot\bootx64.efi" --label "Windows 10"

(after restoring the backup of bootx64 ^)

and I also tried:

sudo efibootmgr --create --disk /dev/sda --part 2 --loader "\EFI\Microsoft\Boot\bootmgfw.efi" --label "Windows 10"

but in both cases selecting this entry on a fresh boot just restarts the machine, and in ubuntu after rebooting the entry shows up as VenHw(some-id-here)

---

### Post by oldfred on 2019-01-22
What brand/model system?
I think I have seen one or two that just boot the fallback entry or bootx64.efi.
And several brands would only boot by correct description and only correct description is "Windows Boot Manager". For those with just Ubuntu we make that the description to boot Ubuntu's shimx64.efi file. And those are often the systems that may also boot the fallback entry also.

       New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Post this:
sudo efibootmgr -v

---

