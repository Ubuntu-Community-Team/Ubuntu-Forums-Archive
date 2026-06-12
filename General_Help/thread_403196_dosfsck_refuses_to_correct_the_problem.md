---
title: "dosfsck refuses to correct the problem"
date: 2007-04-06
forum: General Help
---

### Post by eobard on 2007-04-06
At startup I keep getting a dosfsck "differences between boot sector and backup" error. Now I know how to set it so the error doesn't show, but I'd prefer to remove the inconsistency instead. I've tried to use option #2 (copy original to backup) but it won't work. I get a "Leaving file system unchanged" response. I don't want to put the backup in place of the original because other than the error in Ubuntu the system works fine, so I'm presuming that the problem is with the backup. I've tried running it as su, booting to a maintenance prompt and running it that way, and no go. What do I need to do to get it to actually implement the correction? I'm running 6.10 if that has any influence on your suggestions.

---

### Post by yabbadabbadont on 2007-04-06
Boot windows and let it fix the error.  You may have to manually run chkdsk.

---

### Post by eobard on 2007-04-06
I tried. Windows isn't aware of the problem. Neither is Slackware, which is also on the system. Only Ubuntu sees it.

---

### Post by yabbadabbadont on 2007-04-06
I wouldn't worry about it then.  If checking the drive in windows doesn't find any problem and neither does the dosfsck included in Slackware, then I would guess that it might just be a bug in the version included in your version of Ubuntu.  You might check launchpad to see if such a bug already exists.

---

### Post by eobard on 2007-04-10
Found out a way around it. I used a boot CD with [Gparted]("http://gparted.sourceforge.net/") to slightly reduce the size of the primary partition of the drive in question. I then saved, rebooted and resized the drive to use up the bit of space I had just freed up. In doing so GParted re-wrote the partition table for both the primary and backup.

---

### Post by Malac on 2007-05-08
```
sudo umount /dev/[COLOR=Gray]*<whatever>*[/COLOR]
sudo dosfsck -ar /dev/[COLOR=Gray]*<whatever>*[/COLOR]
``` should do it.

---

### Post by dcstar on 2007-05-09
> **Malac said:**
> ```
sudo umount /dev/[COLOR=Gray]*<whatever>*[/COLOR]
sudo dosfsck -ar /dev/[COLOR=Gray]*<whatever>*[/COLOR]
``` should do it.

That works well - I had the same issue on a USB stick drive and it was annoying me!

---

