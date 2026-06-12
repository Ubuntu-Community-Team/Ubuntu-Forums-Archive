---
title: "Advice on Cache Solution"
date: 2020-06-25
forum: General Help
---

### Post by mikkel4 on 2020-06-25
Hi i need a little advice on what to use as a cache solution..

i have a 12TB MDRaid and a 120GB SSD.

What i want to accomplish: when i download files (torrents) i want it to stay on cache (SSD) so i easily can rename and copy to the right dir without choking because of IO after rename etc i want it to go to my MDRaid

i was thinking about using MergerFS but is there anything better ?

---

### Post by ActionParsnip on 2020-06-25
The non-SSDs aren't that bad and moving stuff around the same disk won't "choke" it. I suggest you setup the 12Tb disk as a separate folder like "/data" in the file system and keep the OS on the SSD. You could even carve a small bit of space out for "/tmp" and put swap on the RAID as well to reduce wear on your SSD.

---

