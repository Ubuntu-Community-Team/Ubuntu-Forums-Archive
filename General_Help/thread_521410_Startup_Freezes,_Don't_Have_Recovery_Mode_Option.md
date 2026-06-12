---
title: "Startup Freezes, Don't Have Recovery Mode Option"
date: 2007-08-09
forum: General Help
---

### Post by BlairHippo on 2007-08-09
I left my Ubuntu machine on overnight, and a power failure turned it off.  Now, I can't get it to start back up.

I'd love to do some kind of recovery mode, but that's not an option; GRUB only presents me with "Ubuntu Linux" and "Windows".  I can do "e" to edit the commands or "c" to just start manually entering things myself, but since I have no idea what to do and haven't been able to find anything about recovery mode other than "Just select recovery mode from GRUB!", they're kind of useless to me at the moment.

When I try to boot Ubuntu, I get some errors ... but I ALWAYS get some errors on this machine.  I get some PCI resource allocation errors, a PCI region update error, some Buffer I/O errors on sdc4, and a couple of "Filesystem is NOT clean" complaints, but that's all pretty much par for the course.  I can type-in the precise errors I'm seeing, but I'd rather not, since I'm pretty sure they're red herrings.

Anyway, after I get what is (for my machine) the usual litany of errors, it goes no further.  Hitting alt-F2, alt-F3, etc. just gives me blank screens.

So, can anybody tell me 1) how to get myself into recovery mode and 2) what sort of things I ought to try once I'm there?

Thanks,
-- Pete

---

### Post by kidders on 2007-08-10
Hi there,

You can roll you own "recovery mode" grub entry on the fly by adding the word "single" to a kernel's boot parameters. Hit "E", as you mentioned, and go from there. The change will only take effect for one boot, so it doesn't matter if you make a mistake.

To be honest though, I would recommend downloading a Linux boot CD of some kind, and booting with that. At least then you'll *know* your system will boot up properly, and you can take a look around to see what's working and what's not. I suggest starting by mounting your filesystems in read only mode, or perhaps running fsck on them, to see if they're okay.

---

