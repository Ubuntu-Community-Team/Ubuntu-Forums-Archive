---
title: "No boot device found. Press any key to reboot the machine?"
date: 2015-09-11
forum: General Help
---

### Post by Milan_Pecov on 2015-09-11
After I made a regular software update on my laptpot (Dell Inspiron 5520 with Ubuntu 13.04), it was completely blocked so I restarted it manually. Then, during the boot process I got this message: "No boot device found. Press any key to reboot the machine?"

Following the instructions from [here ]("http://ubuntuforums.org/showthread.php?t=2190394")I boot the system via Boot-Repair but the default repair is not fixing anything.
Here is my boot info: [http://paste.ubuntu.com/12334400/](http://paste.ubuntu.com/12334400/)

My guess is that the hard-drive is dead because the error I'm getting is: "[COLOR=#000000]no valid partition table found [/COLOR][COLOR=#BB4444]"blkid"[/COLOR][COLOR=#000000] output:[/COLOR]"... so I should probably try adding a new hard-drive

Any ideas what can be the cause for this, and what's the usual way around this problem?

---

### Post by TheFu on 2015-09-11
Support for 13.04 ended in Jan 2014. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) Best to only run LTS releases if you cannot move to the new release every 6 months.

No disks are seen.  Lots of reasons for that. Could be 
* broken/loose cable
* broken disk controller
* failed disk
* loose/broken power cable to the disk

or about 20 other things. Start with those.

---

