---
title: "vino-server CPU usage is too high"
date: 2014-03-26
forum: General Help
---

### Post by squarethumps on 2014-03-26
I am finding that my CPU usage when I connect with remote desktop is so high that it makes the system unusable.  I've read some old posts on bugs in the main loop and this and that that claim to have fixed this, but this is still a problem for me.  I _need_ a solution to this because I'm working away from my office right now and I MUST be able to remote desktop to my ubuntu machine in the office ( It's running a virtual Windows machine with a simulator that I must access )
```

Welcome to Ubuntu 13.10 (GNU/Linux 3.11.0-18-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Linux mybox 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

I'm not sure what other information to provide on this ... 

THANKS for any help that is given.

---

### Post by steeldriver on 2014-03-26
What desktop session are you running? have you tried something less resource intensive (a 2d session, or xfce, or lxde)?

---

### Post by squarethumps on 2014-03-26
I am runing the 2d session as far as I remember.  ( ubuntu classic I think it is? )

---

### Post by steeldriver on 2014-03-26
one other thought... you are tunneling over SSH right? if not (and the machine is exposed to the public internet) it may be going crazy trying to fend off nefarious VNC connection attempts (and filling your logs...)

---

### Post by squarethumps on 2014-03-26
Actually I am using a Cisco VPN client to connect to the main office network, and then I'm using the remote desktop without another ssh tunnel since the machines are on the same network.

---

### Post by squarethumps on 2014-03-26
I am ( now ) running vino-server in "nice" mode .. .which has helped ever so slightly, but it's still extremely slow to react to my keypresses and mouse clicks.

---

