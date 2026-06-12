---
title: "Can no longer access Linux partition after switching to UEFI."
date: 2022-02-12
forum: General Help
---

### Post by Mugsy323 on 2022-02-12
Thank you for clicking my topic.

I've had a Dual Boot setup with Windows and Ubuntu for years, but after "upgrading" to Windows 11, my Ubuntu partition no longer appears in my (Bios) boot menu.

Win11 required me to switch my Bios settings to pure UEFI with "CSM" enabled. My linux partition was created using the old "Bios" and MBR configuration. Now the boot menu doesn't detect anything but my Windows boot drive (linux drive IS visible in Bios, and accessible if I boot using an Ubuntu boot DVD), USB flash drives and my BluRay burner.

Is there a way to boot from my Linux partition again under a UEFI bios? I'm wondering if I simply need to change the boot sector from MBR to "GPT", but I'm afraid I might lose all my data doing this to a linux drive from Windows (and I'm only guessing this is what's needed.) Can this be done from Windows safely (or the Ubuntu boot DVD?) Is this even all I need to do or is there a different fix?

I checked "GParted" but could not find any such MBR -> GPT option.

TIA

PS: Both Windows & Ubuntu are on their own dedicated drives.

FOLLOW-UP. SOLVED: I found a nice simple non-destructive solution. In order to install Windows 11, it required me to disable "CSM" (the Compatibility Support Module) in the BIOS. But I've just discovered that once Win11 is installed, you can simply re-enable it again. Windows still loads fine (I'm in it now) AND my Ubuntu boot drive is visible once again from my Bios Boot Menu (F8). I was able to boot my Ubuntu drive for the first time in 3 months (lots of updates since then) with no loss of data. I hope this helps someone. I wished I had realized that's all I had to do months ago. I could have put myself through a LOT of work for nothing.

---

### Post by oldfred on 2022-02-12
Simple conversion from MBR to gpt erases all partitions on that drive.

If Ubuntu on separate drive, you can convert to UEFI. You convert to gpt but that will change all UUIDs, so you at minimum need to reinstall grub and update /etc/fstab with new UUIDs. You have to add an ESP - efi system partition as FAT32 with boot,esp flags (if gparted).

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

The backups are vital as if any issue, then you will need to do a new install & restore your data, list of apps & maybe other settings or data that are part of your normal backup.
Many find new install & restore from backup to be quicker & easier than major conversions.

---

### Post by Mugsy323 on 2022-02-12
Thx for the reply. Fortunately, I didn't have to go thru all that. Simply re-enabling the CSM in Bios was all I needed to do.

I don't think Ubuntu needs/benefits-from a GPT boot record, so there's no need for it (as least in this case.)

---

