---
title: "Failsafe mode"
date: 2007-07-24
forum: General Help
---

### Post by loki525 on 2007-07-24
I am new to Ubuntu but my son loaded it and I've enjoyed playing with it for the last month or so.  The other night my wife shut off my desktop without closing it down and now it won't start.  I get an error message telling me I have to restart in failsafe mode and fix the problem.  How do I do this? What are the steps?  I've tried looking through the FAQs and other strings but the only references I've been able to come across are completely unintelligible to me.  Is there anyone out ther who can explain what I have to do in a comprehensible manner?  Thanks.  

Ubuntu is the most user friendly distro I've seen and I'd hate to have to give up on it but I can't seem to fix the problem.

---

### Post by Paul S on 2007-07-24
If you did the normal ubuntu installation, on your grub boot screen will be a selection for "recovery mode".  Once you get into a terminal, you probably just need to run "e2fsck" at the root shell prompt.

HTH

---

