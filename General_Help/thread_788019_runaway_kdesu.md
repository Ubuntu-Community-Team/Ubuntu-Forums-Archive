---
title: "runaway kdesu"
date: 2008-05-09
forum: General Help
---

### Post by ZiVvmO on 2008-05-09
So, I built a new machine and put Hardy on it.

So far I have had very few problems.  The biggest annoyance right now is that when I login to KDE (after reboot, X restart, or just logout and login) I have an instance of kdesu that uses 100% of one of my processor cores and does not stop until I kill it.

Is there a way to tell what program is invoking the kdesu?
Any suggestions as to what is going on here?

---

### Post by ZiVvmO on 2008-05-14
Eh?

---

### Post by Zorael on 2008-05-14
Huh, can't say I even know where to begin. No weird apps set to autostart in [FONT="Courier New"]~/.kde/Autostart[/FONT]?

Does [FONT="Courier New"]top[/FONT] list the arguments that kdesu was evoked with?

---

### Post by ZiVvmO on 2008-05-14
> **Zorael said:**
> Huh, can't say I even know where to begin. No weird apps set to autostart in [FONT="Courier New"]~/.kde/Autostart[/FONT]?

Does [FONT="Courier New"]top[/FONT] list the arguments that kdesu was evoked with?
Well, apparently since posting, the offending program has stopped doing whatever it was doing...

It did this for about a week until....just now.  Well, it seems to be fixed at least.  I'll repost if it reappears.

---

### Post by Zorael on 2008-05-14
Sometimes they just need some threatening to fall back in line. :>

---

