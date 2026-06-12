---
title: "Unable to boot Windows after boot-repair"
date: 2013-01-07
forum: General Help
---

### Post by lucas006 on 2013-01-07
Hi.
After install Ubuntu 12.10 (64 bit) on the new partition (other was for Windows 7) grub wasn't showing, Windows 7 was loading automatically. So i read that i should use boot-repair. While repairing, it prompted message "LDM-blocker detected" - I read someone lost all data after choosing "Yes", so I choose "No". After reboot grub shows, Ubuntu loads normally, but after trying to launch Windows 7 it prompts "disk read error".

Here is boot-repair logfile:
[http://paste.ubuntu.com/1506855/](http://paste.ubuntu.com/1506855/)

Please help, lucas006.

---

### Post by oldfred on 2013-01-07
I had never heard of LDM until this bug was posted.
       ldm bug grub2 2.00
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

    
Several work arounds are posted.  Oldfred's suggestion is in post #44. 

Did you  have dynamic disks before?

---

### Post by lucas006 on 2013-01-07
> **oldfred said:**
> 
Did you  have dynamic disks before?

Yes, I had.

//edit
Okay Windows loads! Thanks alot :)

---

