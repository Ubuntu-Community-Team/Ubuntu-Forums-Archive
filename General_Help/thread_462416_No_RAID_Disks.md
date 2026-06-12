---
title: "No RAID Disks"
date: 2007-06-02
forum: General Help
---

### Post by sba99jpd on 2007-06-02
I'm now getting the message "no raid disks" and the installation stops.  Any clues as to what to do?

Cheers!

---

### Post by ago on 2007-06-02
This sometimes happens when you hard boot and the system.vitrual.drive gets corrupted. If you let it run for 5-10 minutes you should get a shell prompt, type 

more /tmp/zenigata.log

---

### Post by sba99jpd on 2007-06-03
Hi,

Thanks for the help so far, but this happens each time I try to boot up; I tried "more /tmp/zeigata.log" and there was some activity, but still no ubuntu.

Can you help further?

---

### Post by The Digital Pioneer on 2007-06-03
I'm having this problem too. I haven't tried the "more" command, because running more on a logfile won't fix any problems, it'll just read the logfile. I'm sure you know what you're doing, and the contents of that logfile will be useful, but I haven't gotten around to rebooting yet, so do you have any other info? :)

---

### Post by dstaudt on 2007-06-03
I had this problem as well.  Inspecting /tmp/zenigata.log, it appears to be complaining that the disk was hibernated and could not be mounted.  While I have hibernation enabled and use it frequently, in this case proper shutdown had definitely been performed before the Wubi startup.

It appears that the mounter is improperly detecting a hibernation state..?

In any case, I disabled hibernation in the XP power control panel (and confirmed hiberfil.sys was removed) and everything worked after that.  I'm posting from Ubuntu now :)

---

### Post by The Digital Pioneer on 2007-06-03
Bah! No excuse for that. How do I disable hibernation checking? I have hibernation enabled, however I did not hibernate to switch to Linux (although that should be implemented ASAP, IMHO) There has to be another workaround for this. My laptop is practically dependent on hibernation. A straight reboot takes windoze for EVER!!

---

