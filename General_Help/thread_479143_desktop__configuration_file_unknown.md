---
title: "desktop  configuration file unknown"
date: 2007-06-20
forum: General Help
---

### Post by Howard Kaikow on 2007-06-20
Booted to ubuntu 7.04.

Used

sudo apt-get --purge remove wxDFast

Opreration completed successfully.

Used Places to open Computer so I could see whether the wxDFast config file had been deleted. Config file had not been deleted.

Opening Computer, for ALL drives and the Filesystem, it states "desktop configuration file unknown".

I tried rebooting, but problem persists.

I can get to all drives, the Filesystem and my directory.

Any ideas on how to fix this?
Or, should I just restore a backup from 18 June 2007?

---

### Post by Howard Kaikow on 2007-06-20
I am am confused, ah, but you already knew that!

The "Desktop configuration file" is listed in the Type column, and "unknown" is listed in the Date column.

So maybe there is no problem.

I had not seen/noticed this before.

Maybe I should just get some sleep!

---

### Post by jwooton on 2007-11-24
I have this same issue...  I'm not sure when it happened.  I'm running Gutsy Gibbon 7.10. with Gnome version 2.20.1.  Just a wild guess was this may have happened after an update...not sure.

When you are under "computer:///" in the File Browser, all drives display as type "desktop configuration file" and Date Modified is listed as "unknown".

However, if you open up System Monitor and go to the File Systems tab you can see disk types...free space...etc.  Also, the "fdisk -l" command lists the correct types as well.

I am attaching a screenshot.

Any ideas?

---

### Post by delivolicita on 2007-12-01
> **jwooton said:**
> I have this same issue...  I'm not sure when it happened.  I'm running Gutsy Gibbon 7.10. with Gnome version 2.20.1.  Just a wild guess was this may have happened after an update...not sure.

When you are under "computer:///" in the File Browser, all drives display as type "desktop configuration file" and Date Modified is listed as "unknown".

However, if you open up System Monitor and go to the File Systems tab you can see disk types...free space...etc.  Also, the "fdisk -l" command lists the correct types as well.

I am attaching a screenshot.

Any ideas?
Same problem.

Looks fine in System Monitor.

bad in File Browser.


Thanks

---

