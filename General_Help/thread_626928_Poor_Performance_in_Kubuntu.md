---
title: "Poor Performance in Kubuntu"
date: 2007-11-29
forum: General Help
---

### Post by Royall on 2007-11-29
I've got a P4 at 2.8 GHz, a gig of RAM, and Audigy 2ZS, and an incredibly powerful GeForce 7800. Whenever I turn on my printer or queue up an MP3 in Amarok, the whole computer stops responding for a good 20 seconds or so, which doesn't make any sense to me. Also, Firefox performance is pretty bad, too. 
Is this the wake of that "completely fair scheduler" I've been reading about?
If so, is there anything I can do besides downgrade my kernel?

---

### Post by cknight on 2007-11-29
Sounds more like some rogue process eating away all of your CPU.  Open a terminal and type the command 'top'.  This will show you a list of running processes and help identify if any are eating away at your CPU.  Then you can diagnose further based on the result.

---

