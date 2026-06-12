---
title: "pendrivelinux legit? UEFI install issues"
date: 2015-10-12
forum: General Help
---

### Post by JamButty on 2015-10-12
Trying to install 14.04 to a UEFI desktop married to Windows10. Most howto pages I find tell me to create a bootable thumbdrive using Pendrivelinux (aka Universal USB installerfrom here - pendrivelinux. com/universal-usb-installer-easy-as-1-2-3/. I tried that, got pages and pages of ads/offers, then some locked-in(automatically regenerating) pages requiring me to blow off Firefox to get out. The site only installed 7zip. No sign of the thumbdrive program. Now that site only redirects to another unrelated page.

Do I need this program to reliably create a UEFI compatible Ubuntu boot thumbdrive? Is there a version that is not Adware? Have been to many pages on this, but find them all either excessively complex, or simple and ALWAYS pointing to this adware Pendrivelinux site.

thanks

---

### Post by oldfred on 2015-10-12
Actually if you want an UEFI only boot flash drive you do not need an installer at all.

You just need to format flash drive with FAT32 and set boot flag on. Then use whatever is your favorite extraction tool like 7zip to extract & copy ISO to FAT32 partition. UEFI boots from a FAT32 partition with a very long GUID (if gpt) to identify it. Gparted and some other tools use boot flag to set that GUID. A few UEFI want flash drive as gpt, most will boot with MBR as even MBR has a code for ESP - efi system partition.

Ubuntu has built in /EFI/Boot/bootx64.efi which really is a copy of grub, for booting in UEFI mode.

Normal installers do the format, extract, but also then install a BIOS boot loader. Ubuntu uses syslinux as BIOS boot loader but with UEFI only you do not need that.

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

            Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

---

### Post by JamButty on 2015-10-12
[INDENT]                     In several places the advice is given to backup the EFI partition.  How? I have no access to that. In the Windows10 system as purchased,  there are 4 partitions:
1. the EFI partition (500MB) no listed file system -inaccessible
2. recovery partition (450 MB) no listed file system - inaccessible
3.2nd recovery partition (11.88 GB) no listed file system -inaccessible
4. OS C drive in NTFS -remainder of drive - accessible

I may be able to create a usable boot/installation (yes, I am installing  for dual boot) thumbdrive with Rufus and turn off the problematic UEFI  features (secure boot, fast startup etc.), but messing with the EFI  partition or renaming any Windows system files does not seem like a  workable solution.                 [/INDENT]

---

### Post by oldfred on 2015-10-12
From Ubuntu live installer in live mode, you can see the other partitions.

When I got a new Dell it insisted I make a Dell backup, a Windows backup and a Windows repair flash drive. It said I could then delete those recovery partitions, but I did not, and now wish I had. I also made a full image backup of Windows with Macrium free. And while I did all that I had no plans to use Windows. But I did in the end as Comcast will not let me see programs via Ubuntu.

In Windows you have to mount the efi partition. I have seen it in some instructions, but I last used XP and barely know anything about Windows 8 or later.
I found this in my notes:
 mount the ESP with `mountvol b: /s` in Windows
[https://technet.microsoft.com/en-us/library/cc772586.aspx](https://technet.microsoft.com/en-us/library/cc772586.aspx)

---

### Post by JamButty on 2015-10-13
Thank you. Have found some leads to help and looked into Macrium. Will post results and close thread once this is finished. It will take quite a while.

---

