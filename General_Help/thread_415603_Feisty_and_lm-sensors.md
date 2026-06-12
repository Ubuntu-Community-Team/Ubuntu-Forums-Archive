---
title: "Feisty and lm-sensors"
date: 2007-04-20
forum: General Help
---

### Post by therunnyman on 2007-04-20
Hi all,

I've got sensors, I know I do, because I've had sensors picked up by lm-sensors (or sensors-detect, rather) since Breezy.  Now I'm being told I have no sensors, by both lm-sensors and mbmon (and xmbmon).  I'm at a loss.

I've exhausted the tutorials, both here and elsewhere on the Internet, and I can't get this thing to work.  Anyone have any ideas, or confirmation of this problem?

runny

---

### Post by fragos on 2007-04-20
Have you run "sudo sensors-detect"?

---

### Post by therunnyman on 2007-04-20
Yes, I did run sensors-detect.  I'm pretty certain I did everything correctly, it's just Feisty being Feisty.

Fled back to Edgy: that did the trick.  I'm thinking, after all the difficulties, I'm just going to skip this iteration.  Skipped Dapper, and I'm still alive.

Thanks for the stab at helping either way!

runny

---

### Post by flyingbrass on 2007-04-20
I presume you added the necessary modules to /etc/modules, but after that did you either load them manually or reboot?

---

