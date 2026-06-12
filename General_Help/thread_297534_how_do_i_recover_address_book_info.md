---
title: "how do i recover address book info?"
date: 2006-11-11
forum: General Help
---

### Post by kellineil on 2006-11-11
Hi

i recently upgraded to edgy - no problem there

but

yesterday i attempted to upgrade my windows installation to xp.  this is on a seperate hard disk.  despite this, the installation failed and at the same time corrupted the previous windows installation and edgy as well.  I'm not entirely sure how this happened but i now cannot log on to edgy.  it appears that the entire user directory in the home directory has been deleted.  there is now no data in the home directory

as a result i've had to reinstall dapper onto another partition.  

my question is, is there anyway i can recover address book information from the thunderbird in edgy?  there are some essential addresses i hold in there.  I can pretty much write off all the other info, but i need the addresses!

thanx

---

### Post by kidders on 2006-11-11
Hi there,

Microsoft OSs can't read Linux filesystems natively, so if XP deleted something, it was probably an entire filesystem :-(

Depending on how much (and what kind of) writing has been done on the affected disk since, you *may* be able to use a forensic data recovery tool to recover some of the original filesystem.

Is there any way you could be more specific about what actually happened?

**Edit:** A missing /home doesn't require a re-install to fix. The most that should be required is an **mkdir /home/<username>** to give KDE/Gnome/etc. someplace to put stuff.

Anyhow, assuming you've lost your /home partition, any of the following will _drastically_ reduce your chances of being able to recover it. With luck, you won't say "yes" to too many of these!

[LIST]
[*]You have changed the shape of your partition table
[*]You have replaced the deleted filesystem with a new one
[*]You have replaced the deleted filesystem with another of the same type
[*]You have written lots of stuff on top of the original location of your /home
[/LIST]

In any case, if you want to try to recover erased data, the most important thing to do is to stop writing to the affected device straight away.

---

