---
title: "TimeShift Issue"
date: 2017-06-13
forum: General Help
---

### Post by jaredseavy88 on 2017-06-13
G'Afternoon! I hope someone can help me out.
I am using Ubuntu Gnome 17.04.  I have been using Timeshift successfully, however I decided to exclude a few folders (Like steam games) to help reduce the amount of space the backups take up. I removed the snapshots and checked my disk usage.  To be expected, my disk usage was much lower (about 76GBs).  Great.  I excluded the folders and began the new snapshot.  During the process I canceled it because I realized I excluded the wrong steam folder.   It now says there is not enough space to create a snapshot.  When I look at "Disks" application it believes that my sdd is at about 205 GBs.  When I look at the "Disk Usage Analyzer," it believes that it is still sitting at around 76GBs.  Is there some hidden folder that the snapshot could have saved to when I canceled?  Any help would be very much appreciated!

---

### Post by jaredseavy88 on 2017-06-13
I've realized what was happening. It is obvious now, but for others that are ignorant to Ubuntu as I am; There is another trash folder in the root directory.  I installed k4dirstat (which seems to be better than "Disk Usage Analyzer") and see that I have 114.56 GBs sitting at /.local/share/Trash.  Problem solved.  Thanks all if you had attempted to help!

---

