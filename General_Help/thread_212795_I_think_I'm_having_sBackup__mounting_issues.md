---
title: "I think I'm having sBackup / mounting issues"
date: 2006-07-10
forum: General Help
---

### Post by talz13 on 2006-07-10
So today my server started acting up, and upon investigation, I found that the root partition was 100% full.  Upon further investigation, it appears that my usb drive became unmounted at some point, and sBackup started writing to the FOLDER "/media/usbdisk/sBackups/" instead of the mounted drive that should be there.  Needless to say, it got through 3 gigs of the backup, ran out of room, and started causing strange problems.

Is there a way to make this not happen?  Like see if the drive is mounted first or anything?  I used to notice that the usbdisk would open a file explorer window from time to time in the GUI, like it would if the drive was just plugged in which makes it look to me like the drive is not staying mounted all the time.

---

