---
title: "Edgy is eating my XFS partitions"
date: 2006-11-15
forum: General Help
---

### Post by TheForkOfJustice on 2006-11-15
Edgy recently went nuts on me and no longer reads my XFS partitions. My /home is xfs and are all of my storage partitions.

I can access neither the internet nor aptitude so it's pretty much screwed (luckily I have other OS's installed).

Edgy will give me a login screen but no longer goes to the desktop. I would call this a problem with my /home being undetectable but it doesn't give Root a desktop either.

Anyone else having partition problems in Edgy?

I also had problems formatting partitions to ext3 with the LiveCD and had to use the gparted LiveCD from Sourceforge. This is probably all related.

---

### Post by TheForkOfJustice on 2006-11-15
After some research I'm beginning to believe my LiveCD-and-installed-system partition format problems may be due to the new UUID implementation and our new fstabs.

I wonder what is being done to fix this.

---

