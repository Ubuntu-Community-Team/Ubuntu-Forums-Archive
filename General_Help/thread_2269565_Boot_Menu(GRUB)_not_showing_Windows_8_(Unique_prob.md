---
title: "Boot Menu(GRUB) not showing Windows 8 (Unique problem, more info in description)"
date: 2015-03-16
forum: General Help
---

### Post by aaronjflores on 2015-03-16
So I have a desktop that I installed multiple OSs on, windows 8 being the original installation. After a week of messing around with it, I ended up with just A windows partition, and an extended partition with a couple of Linux distros and their respective /home partitions. Now, what I don't remember, is what happened to my EFI boot partition, I remember it being their, but I don't remember what I did to it. So, I assumed it was unnecessary as long as I ran boot-repair afterwards. So, when I went to install Lubuntu on my HP Pavilion, at first I just used manual install and resized the windows partition and it installed no problem (I did run boot-repair afterwards bc I installed Ubuntu in Legacy), except that I could not set up the Grub Menu to boot by default, I always had to go into the boot menu and select it, because it was not shown when I go into BIOS setup's boot settings. It would automatically boot into windows otherwise, but windows would show on the Grub menu and it would load fine from there. So I compared my hard drives of my laptop and desktop, and I noticed my Laptop had a EFI partition and a couple other partitions belonging to windows. I installed Ubuntu in Legacy on my desktop, and windows booted just fine without an EFI partition, so I thought if I got rid of the EFI boot partition on my laptop, it would boot straight into grub with windows 8 there, but it did not, and now I can no longer boot into windows (which is bad because I share this laptop with someone who has data on his account.) I should've been more careful, I know. I created a new EFI partition with the correct flag, and ran boot-repair again, but windows is still now showing, and would really like some help :) 
Also, if you could explain to me how windows 8 can boot on my desktop without an EFI parition it would be welcomed information :)

EDIT: After rebooting a few times, not sure what happened, but Windows 8 and it's recovery drive are both showing up in the grub menu, except I cannot boot from either, it brings me to a black screen explaining that the boot file is missing or isn't configured properly.. I guess this has become a windows issue now then?

---

### Post by oldfred on 2015-03-16
Not sure which computer you are discussing?
Best to see details, post link to summary report from Boot-Repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But if you have an extended partition, then you have MBR(msdos) partitioning. Windows and Ubuntu only boot from MBR partitioned drives with CSM/BIOS mode even if hardware has a UEFI boot mode.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

And if drive is gpt partitioned Windows will only boot in UEFI mode. You can install Ubuntu in CSM or UEFI mode from a gpt partitioned drive, but can only easily dual boot if both are UEFI. You have to reboot and sometime have to also change UEFI/BIOS settings to switch from UEFI to BIOS or vice-versa.

If Windows is UEFI all its boot files are in the efi partition on the gpt boot drive. You would have to restore those files using a Windows repair USB flash drive. 
Always good to have a full backup of Windows and the efi partition before installing other operating systems.

---

