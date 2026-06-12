---
title: "CPU always 100% - Probably quick fix. Help!"
date: 2007-03-03
forum: General Help
---

### Post by Tekk on 2007-03-03
I've noticed that my CPU resources are being reported as ~100% pretty much constantly. The gnome task manager shows that it's due to a program called 'pdftotext.' I've tried killing this process both via the manager, and command line - it just pops back up. 

Any thoughts?

Thanks!

---

### Post by t_ras on 2007-03-03
May be you could just uninstall it or delete the bin file (you can see it in process manager in the path).

---

### Post by qamelian on 2007-03-03
> **Tekk said:**
> I've noticed that my CPU resources are being reported as ~100% pretty much constantly. The gnome task manager shows that it's due to a program called 'pdftotext.' I've tried killing this process both via the manager, and command line - it just pops back up. 

Any thoughts?

Thanks!

SOunds like you have Beagle installed. The Beagle daemon uses pdftotext when it's indexing pdf files in you home directory. It should only keep spiking as you describe until it finishes indexing.

---

### Post by Gerard Barberi on 2007-03-03
> **qamelian said:**
> SOunds like you have Beagle installed. The Beagle daemon uses pdftotext when it's indexing pdf files in you home directory. It should only keep spiking as you describe until it finishes indexing.

Which might be forever.  I had Beagle on Edgy once.  It never stopped and when my system went idle, Beagle went nuts.  It hogged all the CPU and wouldn't let go until I took it out of idle.  Like move the mouse or press a key.

---

### Post by qamelian on 2007-03-03
> **Gerard Barberi said:**
> Which might be forever.  I had Beagle on Edgy once.  It never stopped and when my system went idle, Beagle went nuts.  It hogged all the CPU and wouldn't let go until I took it out of idle.  Like move the mouse or press a key.

Wow. I use Beagle and have never experienced any thing like that. I expect it to chew up some resources when it initially builds the index, but I find that it usually only take a couple of hours on my laptop. I just leave it idle while I'm out grabbing a coffee or whatever. After the initial indexing, beagled just naps in the background until it has something to do!

---

### Post by dbera on 2007-03-03
This is probably beagle in action. Beagle recently had a maintenance release 0.2.16.2 which fixes a lot of such CPU problems. There is a ubuntu bug open requesting backport of the fixes to current ubuntu packages.

---

### Post by Tekk on 2007-03-04
Thanks guys, I'm pretty sure Beagle is in fact the issue. I may just wait it out, but I do have a LOT of e-book pdf's for it to sift through.

---

