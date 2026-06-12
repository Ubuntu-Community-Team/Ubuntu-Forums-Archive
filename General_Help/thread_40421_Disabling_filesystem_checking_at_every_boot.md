---
title: "Disabling filesystem checking at every boot"
date: 2005-06-09
forum: General Help
---

### Post by tristan on 2005-06-09
Ubuntu does a filesystem check every boot using checkfs.sh. My partitions are all reiserfs and the filesystem checking (replaying journals etc) takes up at least 50% of the time needed to boot. 

I can remove checkfs.sh from /etc/init.d which will disable checking and speed boot times considerably. However then it's a pain having to manually check filesystems if eg I crash the computer.

Is there a way to make ubuntu check filesystems only every 10th boot (for example)? I've used other distros in the past where this was the case. 

Or can it be made to only do the checking if the system is not shut down cleanly?

Thanks in advance for an help.

---

### Post by defkewl on 2005-06-09
try this:
$ update-rc.d -f checkfs remove

---

### Post by tristan on 2005-06-09
Thanks defkewl, I'll give it a go.

Umm, just before I do though, what will it actually do? :)

---

### Post by darthsabbath on 2006-06-12
Any updates on this thread?  I would like to know what the above command does as well.  I've currently got checkfs.sh disabled, but I'd still like the filesystems to be checked occasionally, just not every boot.

Thanks,
Phil

---

