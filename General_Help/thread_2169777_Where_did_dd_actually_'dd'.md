---
title: "Where did dd actually 'dd'?"
date: 2013-08-23
forum: General Help
---

### Post by samistarii on 2013-08-23
I've been playing around with an Ubuntu install on an old computer of mine and was dd'ing an iso to a usb stick, when I supidly gave the command dd if=xxx.iso of=/dev/usb when it should have been of of=/dev/sdb. Now, dd happily spat out confirmation of its completion and, on realising my mistake, I broke into a cold sweat. Did I accidentally pork my install by writing to its partition. In trepidation I restarted the machine and was pleasantly surprised that it booted perfectly. In fact I have been using it for the past few days and as far as I can tell there is absolutely no corruption whatsoever. So really, my question is what did dd actually do? What happens when one is stupid enough to dd to a directory/file in /dev that doesn't even exist. I initially thought it would start writing out the iso onto the HDD from a sector related to dev but am now not sure. If anyone could give insight into this mystery I would in your debt.

---

### Post by lukeiamyourfather on 2013-08-23
My guess is dd probably made a file called /dev/usb on the hard drive and dumped a bunch of stuff into it because /dev/usb doesn't normally exist on a system.

---

### Post by samistarii on 2013-08-24
> **lukeiamyourfather said:**
> My guess is dd probably made a file called /dev/usb on the hard drive and dumped a bunch of stuff into it because /dev/usb doesn't normally exist on a system. Thanks very much for the reply. Nope, that was the first thing that I checked. I am thinking that dd wrote to empty space, happened not to corrupt anything since the HDD is mostly empty. But since dd just writes straight out, it didn't register a new directory or file. Now as I understand it, the OS will just overwrite the data when it comes across it since it is essentially unaware of it. Not sure if this is what happens but that's the best I can come up with.

---

