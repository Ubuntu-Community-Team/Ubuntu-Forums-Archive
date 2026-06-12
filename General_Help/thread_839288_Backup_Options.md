---
title: "Backup Options"
date: 2008-06-24
forum: General Help
---

### Post by Jesus-Ninja on 2008-06-24
I see that ubuntu comes with sbackup, which ticks all the boxes for my requirements, except one. I wish to run two different backup schedules.

I use an n3200 NAS for all my important data (docs, photos etc) for shared access, including backups of the other systems on the LAN (phones, laptops, media centres etc). I want to backup the ubuntu system to my NAS on one schedule (which I currently am doing incrementally each night, with a full backup every week), but then I also wish to back up the NAS to a 1TB disk in the ubuntu desktop (to get the NAS data off site (the ubuntu system is in a different building: the garage). Of course, the systems won't include the backups of themselves when backing up their counterparts, to avoid recurrence problems.

Complicated enough? :D

So, I need two schedules - one for the Ubuntu to NAS backup, and one for the NAS to Ubuntu backup. Can I do this with sbackup, or do I need something else?

Both backups need to run from the ubuntu system, pushing its own data to the NAS and pulling the NAS data to itself, as the NAS is locked down and cannot be configured to run automated backups.

---

