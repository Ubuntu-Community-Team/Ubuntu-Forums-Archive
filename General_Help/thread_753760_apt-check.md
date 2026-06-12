---
title: "apt-check"
date: 2008-04-13
forum: General Help
---

### Post by sloggerkhan on 2008-04-13
For some reason all my package managers seem broken.
They spawn an apt-cache process which takes over 1 cpu core and never seems to finish.
No idea why or what it is doing....
Is there any way to fix this?
If I kill it, it seems to spawn when  the next package manager I open tries doing anything.

Thanks.

---

### Post by sloggerkhan on 2008-04-13
Thought I'd bump this considering I posted really late at night.

---

### Post by sloggerkhan on 2008-04-14
fixed via the following command:
 sudo dpkg --clear-avail

---

