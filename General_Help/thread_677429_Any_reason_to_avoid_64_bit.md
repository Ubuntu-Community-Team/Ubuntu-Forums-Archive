---
title: "Any reason to avoid 64 bit?"
date: 2008-01-24
forum: General Help
---

### Post by Rahu on 2008-01-24
Just wondering, I've previously only used Ubuntu 32 bit but now I have a 64 bit system that I just put a new hdd in.

Simple question: I only have one gig of ram in that box, so I don't need 64-bit, but I've heard that a 64-bit OS may run slightly faster because I use a 64-bit Processor. Is there any reason at all to use 32 bit over 64?

---

### Post by Zack McCool on 2008-01-24
Compatibility.

In the Linux world, it is a bit less of an issue, but you might find that some devices or applications do not have 64 bit versions, and will not run.

For instance: My laptop's wifi card is a newer Atheros chipset that madwifi doesn't (yet) support.  So, I have to use an NDISWrapper and the Windows driver.  There is not a 64 bit version.  So, if I want my wireless to work, I need to use 32 bit.

Or Flash.  Flash is a binary, and does not have a 64 Bit version.  You can fudge it to work, as I have done on this machine, using a wrapper, but it is not native, and some apps may not have any easy way to get them running.

In Windows, this is much more of an issue.  In linux, most stuff will work fine.

---

### Post by wolfen69 on 2008-01-24
i ran 64bit for a while and didnt notice any difference. i read that in intensive number crunching applications that it can be 30% faster. i think for the average person, 32bit should fit the bill nicely. see this: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

