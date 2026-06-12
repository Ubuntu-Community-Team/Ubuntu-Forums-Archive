---
title: "Power went out during update, boot now fails"
date: 2008-01-07
forum: General Help
---

### Post by OpenSourceFuture on 2008-01-07
Boot up fails at start up, tried reinstalling graphical interfaces in recovery mode, now i get up to a X.org error, it says it has to be manually configured and returns me to command prompt login, which also fails.

More details can be provided upon request, sometime during the boot I get two red [Failed] in the status box in the list of processes starting.

Any help would be greatly appreciated, thank you.

---

### Post by JohnPhys on 2008-01-07
When you boot to recovery mode, are you able to get to a command prompt?

---

### Post by OpenSourceFuture on 2008-01-08
Yes, I am.

---

### Post by tgalati4 on 2008-01-08
Usually you need to perform a manual file system check because there are disk errors that are not easily corrected, or require an intelligent decision.  This is normally not a big deal.

Since you can't do extensive file system repairs when mounted on your root file system, grab a Live CD and boot into recovery mode from the live CD.  Then run fsck.

Something like:

root#  sudo fsck /dev/sda

or

root# sudo fsck /dev/hda  (For Dapper)

Answer yes to most of the prompts then you should be good to go.  Go through the upgrade cycle again to recapture the updates that didn't happen.  

Time to get an UPS.

---

### Post by OpenSourceFuture on 2008-01-08
Thank you very much, I'll try that next.
Ironically I got a UPS the day before, but I had not set it up yet. 
I have since then, experience is a harsh teacher.

---

### Post by OpenSourceFuture on 2008-01-08
I've been on a live usb (backtrack Linux) since I lost Ubuntu. 
Followed your advice unfortunately the partition is clean. Anything other ideas?:confused:

---

### Post by OpenSourceFuture on 2008-01-08
Is there a way to recover my Firefox bookmarks and plug ins?

---

