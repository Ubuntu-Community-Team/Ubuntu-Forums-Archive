---
title: "File-Level Tiered Storage Automation? (High/low watermark)"
date: 2016-01-27
forum: General Help
---

### Post by Justin_Grote on 2016-01-27
Hello,

I have a plex set up with an SSD drive and a mounted Amazon Cloud Drive (with acd_cli) tied together with UnionFS. The idea is to stage new files onto the SSD (they are most likely to be read multiple times when they are new) and eventually destage them to Amazon Cloud Drive (which is slower but good enough for occasional access)

example
/mnt/ssd - SSD Drive (50GB)
/mnt/acd - Amazon Cloud Drive (Unlimited GB)

/mnt/storage - UnionFS with SSD Drive layered on Top of ACD.

So far so good. Now I'm looking for a solution to periodically check the SSD filesystem size, and if it reaches a high water mark that I specify (say 90% full), look for the oldest files (by modify date for simplicity) and move them to /mnt/acd until it reaches a low watermark (say 50% full).

Obviously I can script this and set it up as a cron job but I was just wondering if there is an already existing solution that's probably more robust than what I'd come up with :)

Basically like any Tiered Storage Architecture, but I want to do it at the file level instead of block level (block level would be waaay too slow to try with ACD due to the APIs involved).

Thanks!

---

