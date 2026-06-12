---
title: "need help with vmware"
date: 2006-11-16
forum: General Help
---

### Post by jnev on 2006-11-16
I'm having a problem getting vmware server running on ubuntu edgy (have it running fine on dapper). I installed it normally, entered my serial number and everything, but whenever I try to execute it and start it, my cpu usage spikes to 100% and nothing opens. I have to end the task after that. when I try to open it in the terminal this is my output:

```
jnev@jnev:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

what's wrong, and how do I fix it?


thanks in advance.

---

### Post by FrankVdb on 2006-11-16
Open Synaptic and check whether you have the libraries libdbus-1-2 and libdbus-1-3 installed at the same time. 

If that is the case, remove the oldest one because they don't get along well. Open a terminal and type the following wonderful words:

sudo aptitude remove libdbus-1-2

---

### Post by adzik on 2006-11-19
Thanks FrankVdb.
Your method worked like a charm.
All's good now.
 :D

---

