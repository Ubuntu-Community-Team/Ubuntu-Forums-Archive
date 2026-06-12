---
title: "Updating BIOS via Win10?"
date: 2016-12-26
forum: General Help
---

### Post by Mark_in_Hollywood on 2016-12-26
I have a production Ubuntu 16.04 and a Win10 Recovery thumbdrive. I would like to update the BIOS as the Ubuntu box does not always shut down cleanly. By cleanly I mean sometimes I have to press the power button to get to a power off state. Then, on cold start / power up, I see the cleared inode message.

This is older equipment without UEFI on the motherboard. Currently the 16.04 has no ability to boot from a thumb drive. That is why I want to update the BIOS. The motherboard is HP. 

My question is, running Win10 from a thumb drive, with the Ubuntu box capable to doing a BIOS update?

I can unplug the Ubuntu drive. By the bye: it's a linux only drive, no partitions for Windows. I ask this as I don't want to have the Win10 thumb drive break my Ubuntu 'puter.

Anybody got a clue as to any of this, please?

---

### Post by Frogs Hair on 2016-12-26
Is this a flash type Bios or was there an update utility with the original operating system ?

---

### Post by DuckHook on 2016-12-26
> **Mark_in_Hollywood said:**
> &#8230;By the bye: it's a linux only drive, no partitions for Windows. I ask this as I don't want to have the Win10 thumb drive break my Ubuntu 'puter&#8230;Can you try this out on another experimental box first? Or swap HDDs on your target box with something that is not critical? It's been years since I've installed Windows, so I have no real knowledge about this, but if in doubt, these are the usual precautions.

---

### Post by Mark_in_Hollywood on 2016-12-26
It's an update utility within the Windows OS.

---

### Post by oldfred on 2016-12-27
Most motherboards have multiple ways to install updates.
One is Windows, but then they either support a FAT32 flash drive either DOS booted to run updates or with just the file on it. 
And if just file then from BIOS/UEFI read flash drive.

---

