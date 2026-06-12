---
title: "BOINC not responding in Edgy"
date: 2006-11-04
forum: General Help
---

### Post by cactaur on 2006-11-04
I just installed BOINC v 5.4.9 from the BOINC web site (haven't been able to use the one in the repositories). When I had dapper, BOINC worked very well. However, when I reinstalled my OS, then upgraded to edgy, then installed BOINC, it doesn't work. When I run the boinc manager, the window appears, but doesn't respond. The close button doesn't work, and when I right-click it and say "Exit", it does not respond. I have to open up a terminal and type "killall boincmgr". I'm not sure if I should file this as a bug, but I was wondering if anyone could help me.

ADDITION:When I run BOINC/run_manager, I get
```
send: -1
send: Bad file descriptor
connect: Operation now in progress
```

Then it runs without responding.

---

### Post by epennings on 2006-11-04
I'm using BOINC from the repositories and it works fine for me.
Did you install boinc-manager and boinc-client?

---

### Post by ~LoKe on 2006-11-04
```
sudo apt-get install boinc-client boinc-manager
```
```
boincmgr &
```

---

### Post by cactaur on 2006-11-04
Tried using the one in the repository. Still get the same error, only now, it doesn't run at all. And I have both the manager and client.

---

### Post by jbcola on 2007-10-12
I have the same error, tried to reinstall the mgr, and client -> Still the same error

I've created an empty gui_rpc_auth.cfg file, no change ...

Regards,
Jean-Luc B.

---

