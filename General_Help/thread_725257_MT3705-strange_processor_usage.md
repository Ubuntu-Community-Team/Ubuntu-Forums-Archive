---
title: "MT3705-strange processor usage"
date: 2008-03-15
forum: General Help
---

### Post by Sharpiedeluxe on 2008-03-15
Okay, so I am running Gutsy (feisty kernel) on my gateway MT3705 laptop. I've gotten mostly everything to work fine including audio and wireless. Unfortunately there is this issue where at random times with no apps open, that my processor usage will jump to 100%, and freeze my OS. The interesting about this is my processor is actually not working that hard (no fan turns on). And, when I view "top", no process is using more than 2-3% of my CPU. Anyone have any insight on this problem? Or if I need to post anything like logs then just let me know, thanks a ton.

I found out that this isn't actually the processor causing the problem, rather I think it is the drivers for my hdd controllers. I keep getting the message "hdb: Device not ready for command" in various sectors. Somehow someone said that this was linked to xorg freezing up and that envy would fix the restricted drivers problem. This worked for maybe a few days, but then I got the errors stated above. No I/O errors are problems with specific parts on my drive. Anyone else having the same issue? Or does anyone know if a newer kernel has fixed this problem?

---

