---
title: "Upgrade to 18.04 - Plus new SSD"
date: 2018-11-17
forum: General Help
---

### Post by OBI_Ron on 2018-11-17
Hello Everyone,

Looking for some general guidance...
Situation - backup USB drive trashed - time to upgrade from 16.04 to 18.04

I have 18.04 ISO downloaded and made a bootable usb

I would like to have the os entirely on the new ssd, and us what use to be the main drive for user directories, file storage etc.

Is it better to start with just the sdd in, and boot / install from usb, then add / move use directory later after putting the old hard drive back in?

Or should I simply add the sdd and boot from usb.

Does one way make any more sense than the other?

Thanks in advance for any suggestions / recommendations.

---

### Post by TheFu on 2018-11-17
Ah ... an opinion question.  I love those! ;)

I would install with just the SSD connected if you aren't 100% positive about your partitioning and disk skills.  Lots of people report wiping the wrong disks in these forums.  It isn't hard, but you'll need to "do something else" when the storage options come up AND you'll need to **carefully follow the on-screen instructions.** 
Be certain to setup any required partitions/LVs manually which match whether you have UEFI or BIOS boot setups. I don't use UEFI booting on most of my systems, but there are a number of partitions/LVs needed to make that work. They need to be formatted correctly and the installer needs to know which is for /boot, /boot/efi, /, and probably /home/ ... and perhaps you'll want a separate swap partition. 18.xx switched to a swap file by default, which can be good if there is plenty of room on the disk so it is 100% contiguous and not resized.

Same for the grub install questions.  If you answer incorrectly, you might not have a system that boots post-install.

If you are very comfortable fixing any fstab issues and adding other partitions or logical volumes as desired to that file, then I wouldn't be worried for you.

---

### Post by OBI_Ron on 2018-11-17
TheFu,

Thanks - I was kind of leaning in that direction - doing a minimal install, then adding the old drive and going on from there.  I could very well imagine - as you stated - with both drives in from the start, wiping the wrong one.

---

### Post by oldfred on 2018-11-17
UEFI or BIOS system?
With UEFI much better to follow TheFu's suggestion of just installing to SSD with only SSD connected.
But if newer (last 5 years) hardware it will be UEFI and you can then boot installer in UEFI or BIOS/CSM/Legacy boot modes. How you boot install media is then how it installs.

But even if you want the 35 year old BIOS boot, much better to use gpt partitioning. And to do that you have to partition in advance & choose gpt over the old MBR(msdos) partitioning. But gpt will need either an  ESP - efi system partition (FAT32 with boot flag) or a tiny 1 or 2MB unformatted bios_grub partition. Most of my drives have both, since I started using gpt with BIOS, but now have UEFI.

---

### Post by OBI_Ron on 2018-11-17
oldfred,

Thanks - I just verified using efibootmgr - "EFI variables are not supported on this system."  Old hardware.

---

