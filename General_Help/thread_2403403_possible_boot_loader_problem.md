---
title: "possible boot loader problem"
date: 2018-10-10
forum: General Help
---

### Post by Shinobi_no_mono on 2018-10-10
I did a update back in June and something seems to have gone haywire. What information should I post to receive feedback? It's been years since I had a problem. I have pictures of the possible errors I could post if need be. If I try a recovery with the CD or thumb drive I get nothing, no LiveCD boot, nada........

---

### Post by oldfred on 2018-10-10
You need a working live installer, flash drive or DVD.
You may need to change settings in UEFI to allow USB boot and turn off UEFI secure boot.
Or remake flash drive with current version of Ubuntu.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Shinobi_no_mono on 2018-10-11
thank you Fred, I will try the links above. I know the function to turn off secure boot is disabled "grayed" out and the time in the BIOS is wrong, maybe the battery is just dead but I doubt that would cause GRUB to fail, etc.

---

### Post by oldfred on 2018-10-11
Is this an older system?
Then time error could be battery issue.

And then BIOS will often reset to defaults each time it is powered up, so with most systems you have to change some BIOS/UEFI settings to have it work.

---

### Post by Shinobi_no_mono on 2018-10-11
Asus Maximus viii, i7 CPU, 2-3 years old, flashed/updated BIOS when I first set it up I think, I'm not used to UEFI and grew up on Legacy. I'll remove the battery and reset it or get a new one.

---

### Post by oldfred on 2018-10-11
If only 3 years, battery should not be an issue.
You may need a new update to UEFI then from Asus. And UEFI update will reset some settings. With older BIOS all settings were reset. Now with UEFI only some settings are reset. Usually it remembers boot devices.

My Asus may be similar since about that old also:
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by Shinobi_no_mono on 2018-10-17
I tried the "boot-repair" and that failed, said I was running Legacy even though it's UEFI and I even flashed the BIOS to the latest update. Any other ideas? Maybe follow the steps in this videos? [https://www.youtube.com/watch?v=MN-Q5h2Iv8A](https://www.youtube.com/watch?v=MN-Q5h2Iv8A)

---

### Post by Shinobi_no_mono on 2018-10-17
When booting up from the .iso via usb or cd I'm now able to "try Ubuntu" and see my old drive. I retrieved most of my files but some I still need before doing a fresh reinstall.

---

### Post by oldfred on 2018-10-17
Using Ubuntu live installer run this:

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Shinobi_no_mono on 2019-03-31
I finally got back to trying to fix this, here is the pastebin results:
[http://pastebin.ubuntu.com/p/gCWhTFYgFd/](http://pastebin.ubuntu.com/p/gCWhTFYgFd/)

I remember having a MBR issue years ago, but on a different PC build.

---

### Post by oldfred on 2019-03-31
You are showing UEFI boot.

If you update UEFI from Asus, you may have to redo some settings in UEFI.
I think I have 5 or 7 settings that I change in UEFI, but some are optional. 
And I think the boot mode had to be UEFI only, even UEFI or BIOS did not work.

Some of my Z97 screen shots, yours may be similar since Asus:
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by Shinobi_no_mono on 2019-04-28
I followed your screenshots and made some small adjustments, tried the Boot-Repair again and noticed the same thing as last time:
[HTML]=> No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.[/HTML]

I noticed in GParted the following:
/dev/sda1, EFI System partition, fat32, /mnt/boot-sav/sda1.... flags (boot, esp)
/dev/sda2, blank, ext4, /mnt/boot-sav/sda2.......

---

### Post by oldfred on 2019-04-28
With UEFI boot all the boot files are in the ESP - efi system partition.
You do not want nor need boot files in the gpt protective MBR.

---

