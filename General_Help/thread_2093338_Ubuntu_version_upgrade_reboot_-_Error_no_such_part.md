---
title: "Ubuntu version upgrade reboot - Error: no such partition."
date: 2012-12-10
forum: General Help
---

### Post by pubcrawler on 2012-12-10
Did a routine and long overdue upgrade to our Ubuntu 10 OS on a remote server.

Everything seemed normal and fine.  Was holding back for literally months to schedule a reboot.  Did that this morning.

Upon reboot, nothing.  Remote hands said we are getting an error:
Error: no such partition. 

Our server is fairly generic,  3 drives, boot should be sda.  Other two drives are a RAID setup.

What is the recommended fix for this?  Trying to convey details to remote folks who aren't very tech savvy.

---

### Post by ronparent on 2012-12-10
You don't say what variety of RAID - software, HW or fakeRAID). Also where is the grub located?

My guess for a fakeRAID is that the upgrade didn't include dmraid. If any element required for booting is located on a RAID partition the system won't boot unless the software needed to activate the RAID drive(s) an installed part of the upgrade.

---

### Post by pubcrawler on 2012-12-10
> **ronparent said:**
> You don't say what variety of RAID - software, HW or fakeRAID). Also where is the grub located?

My guess for a fakeRAID is that the upgrade didn't include dmraid. If any element required for booting is located on a RAID partition the system won't boot unless the software needed to activate the RAID drive(s) an installed part of the upgrade.

Yep, RAID is software version - fake RAID.

Grub located? Unsure wherever the default is put.  This is a vanilla install and I didn't install it.

RAID is purely for file storage.  Shouldn't be anything boot time needed there.

---

### Post by ronparent on 2012-12-10
Doesn't look like anything associated with the RAID is causing boot problems. 

At what point during boot does the error occur? I'm thinking possibly a change in UUID of the partition the system was installed on without a corresponding change to fstab?

---

