---
title: "Can't see disks connected to my PCI SATA controller - Drivers needed?"
date: 2007-09-29
forum: General Help
---

### Post by KrisWillis on 2007-09-29
I'm building a file server running Xubuntu 7.04, which is installed on a 13GB drive hooked up over standard PATA IDE. Installed and running fine.

I plugged in a PCI SATA card today, and into that a pair of 500GB drives for my main storage - But I can't see the drives anywhere, I've looked with Gparted and they're not showing up.

I think Xubuntu can see the card, when I run lspci, it notes the following:
```
00:09.0 Mass storage controller: ALi Corporation ALi M5281 Serial ATA / RAID Host Controller (rev a1)
00:09.1 Mass storage controller: ALi Corporation M5228 ALi ATA/RAID Controller (rev c6)
```

Do I need to install drivers to use this card, or is it something else?

Many thanks.

---

### Post by KrisWillis on 2007-09-29
After a bit of messing around, it turns out that one of my SATA cables appears to be faulty - Upon replacement, both drives are being detected.

Thanks for reading, anyway.

---

