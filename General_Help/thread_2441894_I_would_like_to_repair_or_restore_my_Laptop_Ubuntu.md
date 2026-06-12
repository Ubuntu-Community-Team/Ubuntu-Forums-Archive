---
title: "I would like to repair or restore my Laptop Ubuntu GRUB"
date: 2020-04-27
forum: General Help
---

### Post by bhekisizwe on 2020-04-27
Good day everybody

I am having an issue of seeing my Ubuntu GRUB which allows me to choose between the Windows 8.1 and Ubuntu 18.04 operating systems during the Laptop booting sequence. I am using a Lenovo G50-70 Laptop and i have used the USB disk Ubuntu live session to install the Boot-repair utility. The Boot-repair utility sent me this URL "http://paste.ubuntu.com/p/WhVQKRnG6n/" to use in the event that the repair does not work. May you kindly assist me in this regard?

I am not sure whether this is a hard disk drive failure as i am hearing some periodic noise on my laptop on startup. The Laptop eventually says it cannot find the boot media. My laptop has been working fine with the Ubuntu GRUB for the past 4 months. I was able to switch between Windows and Ubuntu OS without any hussles. Then today when i hit the restart button it just all of a sudden stopped working.I think i might have prematurely switched off the Laptop power whilst Ubuntu was shutting down gracefully. Who can help me here because my life is on this Laptop and i cannot access any of my files.

Regards

---

### Post by CelticWarrior on 2020-04-27
Welcome.

The bad news is it can indeed be a drive failure.
But first things first, you should check the boot order in UEFI settings > Boot menu or equivalent.

---

### Post by bhekisizwe on 2020-04-27
I checked the UEFI boot order. The hard drive does not even appear on this boot order. I only see the Fast Boot, USB Boot and Network related Boot. Nothing is mentioned about the Hard Drive. However, under the BIOS information, the Hard Drive Model number does appear but not in the Boot menu.

---

### Post by oldfred on 2020-04-27
Script report only showed sda, your flash drive. No internal drive was seen.
Usually if seen in UEFI/BIOS drive is at least seen.
Is drive set for AHCI in UEFI?
Have you updated UEFI & it reset drive from AHCI to RAID?

Noise, especially from drive is never good.
But I have had wire shift & fan on cpu starts making noise. Or bent  fan cover (who knows how) so it started to tick.

---

### Post by bhekisizwe on 2020-04-27
Yah, the noise is from the HDD. I removed the HDD and the noise disappeared. Re-installed the HDD and the noise started again. How do you update UEFI?

---

### Post by oldfred on 2020-04-27
If really old system, it is BIOS.
But many vendors still call UEFI as BIOS. And UEFI has CSM, a BIOS boot mode for backwards compatibility.
Mircosoft required all vendors to install Windows 8 in UEFI/gpt boot mode in 2012.
So if system older than 2012, then BIOS only.

Vendors vary how to update UEFI/BIOS.
The all update from Windows. Some update from a DOS bootable flash drive with update file. 
Newer UEFI also update from a FAT32 formatted partition that has the update file.
You have to check with vendor & see if the version in your system is newest available. See vendor & its support page for your system.

If drive is failing, may be time for a new system also? Although drives are a lot cheaper now.
Some very old systems do not support very large drives also.

---

### Post by bhekisizwe on 2020-04-27
I would really like to recover my data in my old HDD. Is that possible???

---

### Post by yancek on 2020-04-27
If the drive isn't recognized in the BIOS, I don't think there is much hope of it being recognized by the operating system and if that doesn't happen, you won't be able to access anything.  Have you tried turning off fastboot?  It's situations like this that  require planning which means doing backups.

---

### Post by maestrobwh1 on 2020-04-27
If it is sata, you could try connecting it to a cheap SATA to USB converter cable and see if you can "see" it on another computer or if booted from a USB device on the one you have with the potentially bad drive.

There is a freeware program for Windows and MacOS called "disk drill."  Looks promising IF the disk spins up.  if you recover the data, get an SSD.  I have NEVER had one fail.  I have had plenty of traditional hard drives fail.

---

### Post by bhekisizwe on 2020-04-28
Yah no...i think it is best i just take my Laptop to a data recovery specialist company. Its a very expensive exercise but i have no choice. Somethings were back up...and some were not. Also, who can assist me with getting enabling audio/sound in my USB booted Ubuntu Live session?

---

