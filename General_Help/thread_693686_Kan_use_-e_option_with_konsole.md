---
title: "Kan use -e option with konsole"
date: 2008-02-11
forum: General Help
---

### Post by bigblop on 2008-02-11
I have installed Kubuntu 7.10. When I type:

konsole -e 'ssh [email]root@xxxx.vs.webtropia.com[/email]'

I get:

kdecore (KProcess): WARNING: _attachPty() 11
konsole: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..

And a message pops up with:


Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices.

If I do the same with xterm it works fine:

xterm -e 'ssh [email]root@xxxx.vs.webtropia.com[/email]'

Is this a bug in konsole?

---

### Post by domino1241 on 2008-05-06
bump, exact same problem

---

