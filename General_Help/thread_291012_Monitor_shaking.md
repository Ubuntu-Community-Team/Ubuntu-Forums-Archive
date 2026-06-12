---
title: "Monitor shaking?"
date: 2006-11-01
forum: General Help
---

### Post by WetWired on 2006-11-01
... and still nothing happens. I've tried changing the refresh rate, or rather adding one to xorg.conf, since it appeared to be lacking one, and I've tried degausing it, and it still does it. Almost to the point that it gives me a headache. Any ideas?

---

### Post by Joe_CoT on 2006-11-01
Are you sure the refresh rate is correct? It may be that your driver simply can't refresh the screen fast enough. Which video card are you using (nvidia,ati, other)? Have you tried using its binary driver. Have you tried adding a [modeline](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)?

---

### Post by matthewstory on 2006-11-01
i had a similar problem once . . . are you sure you're not near any high voltage AC lines?  hehe, this was my problem at least.

---

### Post by WetWired on 2006-11-02
AC lines was my first guess too, but I'm dual booting with Windows XP and Ubuntu, and Windows doesn't do it. So I'm figuring it's something in the configuration on Ubuntu. I'm using an Nvidia GeForce FX 5200, and I THINK i have the nvidia drivers installed. I'll check that when I get off of work today. I'll also try the modeline when I get home. Surely one of them will fix it, and I'll post here again and let you know which one worked.

---

### Post by WetWired on 2006-11-02
Well, niether of those worked... I'm at a complete loss.

---

### Post by WetWired on 2006-11-02
I've found that a refresh rate of 60 stops the flickering, but I'm unable to set it at the resolution I want. I could be doing it wrong though.

---

