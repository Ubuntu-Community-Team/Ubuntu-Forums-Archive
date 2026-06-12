---
title: "Problem booting into Ubuntu (fsck)"
date: 2006-11-27
forum: General Help
---

### Post by flackboy on 2006-11-27
Hi everyone,
   Forgive me if this is a dumb question, but I've started having a problem booting into Ubuntu.  I had a Samsung laptop, which duals boots Edgy and XP.  I've had no problems with it at all since upgrading from Dapper, however I noticed that fsck was being every time I booted up.

Now the boot process pauses indefinitely at the fsck check.  It accesses the disk for a few seconds and then stops dead.  

I can't seem to CTRL C out of the check before it happens - and it then needs a hard reset.

Can anyone help with an explanation of what might have happened and help me get things back up and running?

Many thanks,

Brian...

---

### Post by flackboy on 2006-11-27
P.S.  Forgive the horrible typos.  Writing this on a PC at work with very strange keyboard... B.

---

### Post by PWill on 2006-12-04
Did you solve this yet?
Try letting fsck run for about 5 minutes, see if it gets any further.

---

### Post by wgscott on 2006-12-04
An entry like

/dev/hdc1       /               ext3    defaults  0       1

in /etc/fstab  says to run fsck on it (first), and 

/dev/hdc1       /               ext3    defaults 0 0

says to skip the fscking operation.

---

