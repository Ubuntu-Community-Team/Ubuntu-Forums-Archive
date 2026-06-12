---
title: "I think some drives in a software raid 5 6.06 box have died.  Of something strange"
date: 2007-12-21
forum: General Help
---

### Post by beerorkid on 2007-12-21
I have 5 drives set up in a software raid 5 6.06 setup and have it sharing with samba on my small home network for a few years now.
I mount it on my main gusty box in fstab and it has worked well through earlier versions.
The NAS as I call it has not seen an update for about a year.  It just runs and works pretty well as a network share.

It started acting pretty flaky a few days ago.
If I log onto it I can browse files fine, but am not able to scp stuff to my main puter.

On my main puter which the share is mounted it will freeze up if I try to copy anything over.

I have most of the stuff backed up to an external HD, but am wondering a few things.  So not a major loss.

How can I tell if a drive died on the NAS?

And can anyone help me diagnose the issue?  Like commands to see the health of the drives.

Thanks.

---

### Post by Ocxic on 2007-12-21
check the man page for mdadm

"man mdadm" in a terminal.

---

### Post by beerorkid on 2007-12-21
I figure I need the --monitor flag.  Will do more research.

Thanks for the tip :)

---

