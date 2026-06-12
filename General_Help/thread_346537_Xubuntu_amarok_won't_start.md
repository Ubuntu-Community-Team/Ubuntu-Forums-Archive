---
title: "Xubuntu amarok won't start"
date: 2007-01-25
forum: General Help
---

### Post by toran on 2007-01-25
OK, so I'm on Xubuntu, and I'd like to use amarok. I installed it with "sudo aptitude install amarok". Anyway, it installs all the dependencies and stuff, so I try to start it, but it crashes on start with the following error:

```
jon@gimli:~$ amarok
Floating point exception (core dumped)
jon@gimli:~$ 

```

Strange, I thought, I've never seen that problem. So I try a "kdeinit" at the command line (I'm in xfce) to see if that is the problem.

```
jon@gimli:~$ kdeinit
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/jon/.DCOPserver_gimli__0
and start dcopserver again.
---------------------------------

kded: ERROR: Communication problem with kded, it probably crashed.
jon@gimli:~$ 

```

anyway, googling that error hasn't come up with anything related to my problem, so I was hoping you guys could help!

Thanks in advance.

---

### Post by toran on 2007-01-27
bump

---

