---
title: "Revert apt-get upgrade"
date: 2014-07-12
forum: General Help
---

### Post by cranerja on 2014-07-12
Hi I'm wondering if there is a way to revert an upgrade, preferably from a specific ppa.
For some background, I'm using the oibaf ppa for my video driver and every couple updates, it has problems. I need it for gaming and I'm fine waiting a few days but I'd rather be able to control what version I'm using.

---

### Post by grahammechanical on 2014-07-12
We stop updates from a PPA by disabling the PPA or even removing it in Software and Updates.

Regards.

---

### Post by cranerja on 2014-07-12
Thank you for your response!
 I believe I understand how to stop updates, but what I'm trying to accomplish is being able to roll back an update whenever the new update doesn't work. I tried installing the .debs found in /var/cache/apt/archives for today's date but to no avail.
s date but to no avail.

---

### Post by oldos2er on 2014-07-12
The program *ppa-purge* will disable a PPA and revert any packages back to ones in the default repositories.

---

### Post by cranerja on 2014-07-12
I want to keep the ppa but rollback after an update that doesn't work.

---

### Post by monkeybrain20122 on 2014-07-12
You can roll back all the way with ppa-purge but that is not what you want. I don't think you can just roll back to last update, say yesterday.

I also use oibaf's ppa but I clone my / partition with fsarchiver  regularly (about 12 G, quite fast to clone and restore) and simply restore an earlier image in case an update blows up. 

It updates everyday if you don't want that just go to synaptic and uncheck the ppa's box in System > Repositories > Other Software. I stop upgrading from the ppa when I hit a sweet spot.

---

### Post by ian-weisser on 2014-07-12
You can roll back a single package using dpkg...however you should read the manpage before trying it. Results are neither guaranteed nor supported, and it may break your system.

apt-get has _no_ way to rollback a group of packages...because it relies on dpkg.

If you do not trust a PPA, then either do not use the PPA at all, or use frequent backups that you can safely restore from.

---

