---
title: "Firestart unexpectedly unload if amule is running"
date: 2008-05-12
forum: General Help
---

### Post by ubuscout on 2008-05-12
How I write above, that is the problem I get when load amule with firestart on, have anybody got this problem... ?

thx

---

### Post by hermes0710 on 2008-05-12
Could you start both apps from terminals and post the output when firestart unloads?

---

### Post by ubuscout on 2008-05-12
> **hermes0710 said:**
> Could you start both apps from terminals and post the output when firestart unloads?

...here I am...

ok, I tried to launch first firestarter and then amule by console...


<someone>@<something>:~$ sudo firestarter
Firewall started

***MEMORY-ERROR***: firestarter[25769]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)
<someone>@<something>:~$ 

-----------------


<someone>@<something>:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
Loading temp files from /home/<someone>/.aMule/Temp.
HTTP download thread started

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/<someone>/.aMule/Incoming/ shared
HTTP download thread ended
Host: amule.sourceforge.net:80
URL: [http://amule.sourceforge.net/lastversion](http://amule.sourceforge.net/lastversion)
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

-------------


That is what I get...  Firestarter load without problem as amule... but after a while it stop with that error...


...pls note that without amule loaded it seem firestarter keep on without problem...


thx hermes0710 for all :)

---

