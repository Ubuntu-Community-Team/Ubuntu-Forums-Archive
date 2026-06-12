---
title: "Teamspeak Server issues"
date: 2007-04-03
forum: General Help
---

### Post by Stormweaver on 2007-04-03
Hey guys --

Trying to start up a Teamspeak server here from home on my server machine..

Running a AMD 64 Bit Proc, Ubuntu Edgy (AMD64)

I was getting ready to start up the program when this little error occured.

stormweaver@Hurricane:~/tss2_rc2$ ./teamspeak2-server_startscript start
starting the teamspeak2 server
libgcc_s.so.1 must be installed for pthread_cancel to work
./teamspeak2-server_startscript: line 7:  6474 Aborted                 (core dumped) ./server_linux -PID=tsserver2.pid
stormweaver@Hurricane:~/tss2_rc2$ 



Can anyone enlighten me as to whats wrong?

Thanks!

Stormweaver

---

### Post by Maestro23 on 2007-04-03
It's telling you it needs libgcc.so.1.  You need to install the libgcc1.

Synaptic and search "libgcc1". Mark for installation.

---

### Post by Maestro23 on 2007-04-03
It's telling you it needs libgcc_s.so.1  You need to install the libgcc1.

Synaptic and search "libgcc1". Mark for installation.

or in Terminal:

> sudo update
sudo aptitude install libgcc1



---

