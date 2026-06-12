---
title: "How do I install my ATI Radeon 7000 Drivers within VMware running Windows98?"
date: 2006-08-24
forum: General Help
---

### Post by UltraSonicSite on 2006-08-24
"Setup was unable to find components that can be installed on your current hardware or software configuration. Please make sure you have the required hardware or software"

I'm running VMware tools with the vmware video drive, but I want to install the Radeon 7000 driver.

---

### Post by eternalsword on 2006-08-24
VMware uses the host OS's software for hardware devices AFAIK.  So I don't think it's possible to run the windows Radeon drivers

---

### Post by peabody on 2006-08-24
Yes you have to understand that the windows within vmware is not seeing the radeon card but the virtual device that vmware has setup for it.

What are you trying to do?  Games?  AutoCAD?  Maya?

---

### Post by UltraSonicSite on 2006-08-24
Some simple games, yes :P

---

### Post by peabody on 2006-08-24
You're best bet is Wine/Cedega.  Or dual boot.

---

### Post by UltraSonicSite on 2006-08-24
can I set a dual-boot without having to reformat ubuntu?

---

### Post by peabody on 2006-08-25
> **UltraSonicSite said:**
> can I set a dual-boot without having to reformat ubuntu?



gparted on the Live CD can probably resize your partitions.  Be sure to backup though!

---

### Post by rbmorse on 2006-08-25
Does gparted do NTFS?

---

### Post by eternalsword on 2006-08-25
you can just resize the ubuntu partition, leaving the empty space with the same filesystem.  The windows installer will take care of formatting NTFS.  be sure to read up on restoring grub after a windows install.

---

### Post by UltraSonicSite on 2006-08-25
alrighty I'll try it.

---

### Post by UltraSonicSite on 2006-08-26
windows 98 wont install. I resized my 150GB main partition to about half, so that windows can use the new space, but the cd displays an error when attempting to format the drive. What to doo.

---

### Post by UltraSonicSite on 2006-08-26
What to doo.

---

### Post by eternalsword on 2006-08-26
what does the error say?

---

### Post by UltraSonicSite on 2006-08-26
It's pretty vague, just something along the lines of

"Setup could not format this drive
exiting setup"

I selected the main drive in gedit, and just resized it to about half it's size, so now there is a grey free area. Maybe I have to format it to something before windows 98 can format it to something else?

---

### Post by eternalsword on 2006-08-26
If it's windows 98, it should be able to install to FAT32.  You can try reformatting that partition in gparted to FAT32.  Then you shouldn't need to format it using the setup disc.

---

### Post by peabody on 2006-08-27
> **UltraSonicSite said:**
> windows 98 wont install. I resized my 150GB main partition to about half, so that windows can use the new space, but the cd displays an error when attempting to format the drive. What to doo.

You need to format the partition outside of the install.  FAT32 can accomodate up to 4TB I believe, but Windows refuses to fromat more than 20 gigs or so for the install.

---

