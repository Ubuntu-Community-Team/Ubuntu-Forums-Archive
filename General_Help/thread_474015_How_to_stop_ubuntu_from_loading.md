---
title: "How to stop ubuntu from loading"
date: 2007-06-14
forum: General Help
---

### Post by HgBoy on 2007-06-14
I am trying to remove ubuntu from a computer, and install xp (major hardware issues). The Xp is on a restore DVD (for a laptop). When I put the DVD in the drive and hit restart, the Grub loader ignores the dvd and starts up ubuntu anyway. I can disable the harddrive, but then XP cant find a hard drive to connect to. How do I disable ubuntu to allow the OS change?

---

### Post by jasonlfunk on 2007-06-14
You should be able to change the boot order in your BIOS to boot from the DVD first and then from the hard drive. This will get the DVD to boot and not lose access to the Hard drive.

---

### Post by HgBoy on 2007-06-14
I just disabled the ide hdd boot option, and have the cd/dvd drive set to 1sy boot device. Grub loaded instead. what now???

---

### Post by dreadlord_chris on 2007-06-14
First of all - is this restore DVD actually for the computer you are trying to put XP on? Sorry if this seems like a stupid question, but you wouldn't believe how many people have tried it.

Second - when you changed the boot order in the BIOS, did you press F10 to save the changes?

And third - often times after changing the boot order in the BIOS a **hard reset** is necessary for the change to "take" - in other words, after changing the boot order and saving the changes - turn the computer off then restart it.

---

### Post by HgBoy on 2007-06-14
Yes to all the questions, sort of. The disc is for a gateway laptop with all of the drivers and settings. But the copy my dad has is for my brothers identical laptop. Would that make a difference? I already sent my copy for my old laptop to my dad, but I didnt know it was that specific about the computer.

---

### Post by dreadlord_chris on 2007-06-14
> **HgBoy said:**
> Yes to all the questions, sort of. The disc is for a gateway laptop with all of the drivers and settings. But the copy my dad has is for my brothers identical laptop. Would that make a difference? I already sent my copy for my old laptop to my dad, but I didnt know it was that specific about the computer.

Yes, quite often they are tied to the machine...

---

### Post by HgBoy on 2007-06-14
Ok. Just in case the right disc doesnt work either, is there a way to just completely wipe the hard drive and *then* install XP?

---

### Post by dreadlord_chris on 2007-06-14
> **HgBoy said:**
> Ok. Just in case the right disc doesnt work either, is there a way to just completely wipe the hard drive and *then* install XP?

Yup, you can do this from the Ubuntu LiveCD - just delete the partitions

---

