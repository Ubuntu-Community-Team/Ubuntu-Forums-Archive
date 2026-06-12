---
title: "[SOLVED] linux - backing up data"
date: 2008-02-22
forum: General Help
---

### Post by Rytron on 2008-02-22
Hi,
When I was using xp pro, it was easy to backup installers for applications,games,portable software to an external hard drive; this does not seem to be the case with ubuntu -- is there an easy method to backup all downloaded software,games, etc to an external hard drive in case of your pc crashes/is stolen/lost?

Also just one more thing - if I was to backup everything from linux onto an external hard drive -- I presume that external hard drive would need to be formatted in ext instead of ntfs?

Any adive would be great.

Thank you.

Bye.

---

### Post by Sam Lars on 2008-02-22
If you search Synaptic, you will find a lot of backup applications.  Personally, I use rsync, because it's fast and it does what I want it to, and I can script it into a program how I want it...
As long as you can write to it, it should be fine.  EXT should be more native and more reliable, but I don't think NTFS would end up being bad.

---

### Post by Rytron on 2008-03-05
Hi Sam Lars,
I installed rsync.
When I go to usr/bin/rsync It wont execute?
Please help.

---

### Post by aysiu on 2008-03-05
If you use *rsync*, the external drive would have to be Ext3, yes.

And you do not need to "go to" anywhere to execute *rsync*.

Read more here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Rytron on 2008-03-05
Thank you aysiu,
Great avatar by the way.
I adore cats.

:)

---

