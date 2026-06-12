---
title: "Software raid5 - what if the standalone master drive fails?"
date: 2008-02-22
forum: General Help
---

### Post by clove on 2008-02-22
Using the excellent howto I found [[COLOR="Blue"]here[/COLOR]]("http://bfish.xaedalus.net/?p=188"), I set up a new media server in the following configuration:

Drive 1: Standalone (non-raid) master drive with Ubuntu Gutsy & mdadm
Drives 2-5: Software raid5 array for file storage

Everything is working great so far.

My question is what will happen if the master (standalone) drive fails?  If I put in a new master drive with a fresh Ubuntu install, what will I need to do for it to recognize the raid array?  Is a copy of the mdadm.conf file the only thing I would need in order to restore the raid configuration?

---

### Post by fjgaude on 2008-02-22
If you have to re-install all you need is what you suggested: put the mdadm.config file in /etc/mdadm folder. Failing this you can simply --assemble the array in mdadm program.

I move my main raid from computer to computer and kernel to kernel without issues.

---

### Post by clove on 2008-02-22
Excellent...thanks for the reply.  I'll keep a backup copy of my mdadm.conf on hand.

---

