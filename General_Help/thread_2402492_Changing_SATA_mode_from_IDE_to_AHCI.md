---
title: "Changing SATA mode from IDE to AHCI"
date: 2018-10-01
forum: General Help
---

### Post by Dennis N on 2018-10-01
Can the SATA controller be changed from IDE to AHCI after Ubuntu installation so that the disk then boots in AHCI mode? I ask because while reading about this, I found a few warnings like the one below which applies to Windows, but is it also true for Linux?
> HP recommends setting the SATA Controller Mode BEFORE installing the operating system. Changing the mode after installing the operating system can prevent the system from booting.

---

### Post by oldfred on 2018-10-01
I think the issue was more with Windows.
Lots of new systems use RAID or Intel SRT setting which does not work with Desktop Ubuntu installer. But then you have to install AHCI drivers in Windows first.

Back when I had XP, system was using IDE. And Windows XP would not boot with AHCI. And for it, you had to slipstream the AHCI driver into the install process (somehow). But I had a new small SDD and trim would not work with IDE, only AHCI. So I retired XP, the one app I was still using was not worth the hassle.

---

### Post by Dennis N on 2018-10-01
Background: Last evening, I installed an SSD into my 10-year-old BIOS computer that has been running Linux for years with regular HDD. After installing the SSD, the new installed Ubuntu booted and ran ok but broke the boot splash with tons of warning/error messages. I googled on some of the errors and some discussions mentioned AHCI having a role in this. I looked at BIOS settings, and was surprised this machine had been on IDE mode since day one. I switched to AHCI and restarted, but got same messages again on startup. 

To answer my own question, I just did a test install this morning in another logical volume with the same ubuntu installer with AHCI on, and those warning/error messages went away on reboot. Did a couple of restarts, and all seems OK now. It seems system had to be set to AHCI before install, not afterwards to get this set up correctly.

---

