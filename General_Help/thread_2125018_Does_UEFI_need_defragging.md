---
title: "Does UEFI need defragging?"
date: 2013-03-12
forum: General Help
---

### Post by TNAFan on 2013-03-12
I just picked up a new laptop, and it has UEFI like all of them now (terrible invention btw, why reinvent the wheel?) and apparently it needs a boot partition that is fat32 in able to work.  Normally, Linux woldn't need defragging of course, however fat32 isn't really a standard Linux format.  Fat32 generally needs to be defragged as far as I know.  Is it the same under Linux?  Do we now have to worry about fragmentation? Why, or why not?  This worries me.

---

### Post by cool110 on 2013-03-12
No, as the EFI System partition only contains bootloaders it will not be writen to enought to get significantly fragmented.

---

### Post by varunendra on 2013-03-12
> **TNAFan said:**
> I just picked up a new laptop, and it has UEFI like all of them now (terrible invention btw, why reinvent the wheel?) and apparently it needs a boot partition that is fat32 in able to work.  Normally, Linux woldn't need defragging of course, however fat32 isn't really a standard Linux format.  Fat32 generally needs to be defragged as far as I know.  Is it the same under Linux?  Do we now have to worry about fragmentation? Why, or why not?  This worries me.

Details on UEFI : [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Basically it is just a replacement for the traditional BIOS. It has nothing to do with the filesystem on the disk.

As for your worries with fat partition, it contains read-only files (afaik) which are written only once, while installing an OS, and then are only read each time the OS boots. Since there is no repetitive writing, there is absolutely no chance of fragmentation.

As a side note, the files are only needed to boot the installed OS, thereafter they are not touched. So even if you 'intentionally' cause some dirty mess of fragmentation there, it would have no effect on performance nor booting. ;)

Hope it answers your questions. :)

---

### Post by TNAFan on 2013-03-12
Thanks guys!

---

