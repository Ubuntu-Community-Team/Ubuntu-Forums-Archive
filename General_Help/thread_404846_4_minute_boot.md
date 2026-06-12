---
title: "4 minute boot"
date: 2007-04-08
forum: General Help
---

### Post by Falius on 2007-04-08
Im using an acer aspire 5600 with a dual boot XP/Ubuntu Edgy Eft 6.10 installed for the first time this weekend. Its booting to the login screen taking 3-4 mins, progressess bar stuck in one place.

I looked at /var/log/messages.log :
```

---
Apr  8 17:15:29 ubuntu kernel: [17179587.868000] EXT3 FS on hda3, internal journal
Apr  8 17:15:29 ubuntu kernel: [17179755.504000] pcc_acpi: loading...
---

```
..assuming the numbers are seconds, this is the step causing the bottleneck. The other two slow steps are around 10s each. hda3 is the linux partition on my harddrive.

I looked at the forum and tried the 'notsc' addition to the boot menu but that caused a kernel panic. Anyone have any advice on how to reduce the load time, otherwise I'll have to make a cup of coffee every startup.
Thanks 
Dan

---

### Post by LenzM on 2007-04-09
The beginning of the line is the time each thing is logged and they were both logged within 1 second, so this isn't where the problem is.  I don't know anything more, just thought I'd throw that out there.

---

### Post by laidback on 2007-04-09
Suspect that HAL is stalled attemping to identify some of your hardware, but I'm afraid I cannot say more than that. Could it be the internet connection? I had a similar problem loading Suse10.2 and that is what their forum suggested. If it's possible to identify the hardware you might decide that you could disable it for a trial run without it. 
This is worth a read
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

