---
title: "How to image a RAID 5 array?"
date: 2014-04-21
forum: General Help
---

### Post by Tony_Lillie on 2014-04-21
There seem to be a variety of methods available to image a single standard HDD with Clonezilla leading the way, but when the issue is a RAID 5 Clonezilla is useless, and there is no apparent alternative. I've seen some mention of using the "dd" commands, but once again the documentation (that I found anyway) was exclusively focused on single HDD's.

To be more specific, I'm dealing with a small 3 disk software RAID 5 (as in no controller and not run off the mobo--as in created with Ubuntu alternate install), and it contains the OS (Ubuntu 14.04), so obviously it's bootable. Also, this is NOT a mission critical installation. I created this unit specifically for experimentation, and figuring out a way to image a RAID 5 successfully is at the top of my list.

I'm not afraid to use DD, but I really need some guidance if I go that route. The solution does not need to be gui, but it does need to be possible to automate it with cron or something.

---

### Post by Tony_Lillie on 2014-04-22
Anyone have any thoughts on using DD to individually image each disk? Any success stories, or nightmare failures would certainly be educational.

What about LVM? I don't have my current array set up as an LV, but I've been wanting to experiment with that as well. Most people indicate that snapshots are really easy to take and manage, but it's unclear to me if it's possible to take a snapshot of a bootable partition or a RAID 5 array. Anyone want to chime in on LVM?

---

