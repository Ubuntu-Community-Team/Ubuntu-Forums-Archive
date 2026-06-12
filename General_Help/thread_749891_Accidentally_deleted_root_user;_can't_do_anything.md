---
title: "Accidentally deleted root user; can't do anything"
date: 2008-04-08
forum: General Help
---

### Post by Uninverted on 2008-04-08
It's a long story, but I accidentally deleted the root account. Sudo doesn't work, and I can't access practically anything. This creates a chicken & egg problem, because I need root access to obtain root access. I almost wrote a C program and used fprintf(), but I doubt the OS would let me do that. I can't even access the internet (posting this from another partition).

---

### Post by amrclutch1 on 2008-04-08
To be completely honest I don't think you have a chance to recover root. The only way I can see it as if there was a way to run from a livecd distribution and use root on that to add a root account to your partition? That may make no sense or even be practical, just throwing out ideas.

---

### Post by Uninverted on 2008-04-09
> **amrclutch1 said:**
> To be completely honest I don't think you have a chance to recover root. The only way I can see it as if there was a way to run from a livecd distribution and use root on that to add a root account to your partition? That may make no sense or even be practical, just throwing out ideas.

Ah! That might work. I did install from a CD, so I have access to a live CD. I'll try that and post the results.

EDIT: If I don't post again, assume I made everything even worse.

---

### Post by Iowan on 2008-04-09
CD is probably easier... I *have* used [TOMSRTBT]("http://www.toms.net/rb/") to change the root password on a system I acquired.

---

### Post by Uninverted on 2008-04-09
Right, doesn't seem to be working. I'm going to keep trying, but I might need a reinstall (not really any important data in there). Anyone know any specific files need to change a password or add a user (root exists now, but no/unknown password)?

---

### Post by Iowan on 2008-04-11
There's a **shadow** file that will need to be edited. To be honest, I'd need to check one of my machines to see if **root** has a password assigned - because the account is disabled by default, it *may* not have one. I presume you've tried booting in to recovery mode?

---

### Post by Uninverted on 2008-04-12
Yep; recovery mode is no better than a normal boot.

---

### Post by Tyke91 on 2008-04-12
you don't need root access to copy data to a flash drive (although you may need it to mount a flash drive if you're not in the right group...) is backing up your data and reinstalling out of the question?

---

### Post by Uninverted on 2008-04-13
> **Tyke91 said:**
> you don't need root access to copy data to a flash drive (although you may need it to mount a flash drive if you're not in the right group...) is backing up your data and reinstalling out of the question?

No. That's probably what I'll need to do. *sigh*

EDIT: Alright, reinstalled. It's working fine besides the usual quirks.

---

