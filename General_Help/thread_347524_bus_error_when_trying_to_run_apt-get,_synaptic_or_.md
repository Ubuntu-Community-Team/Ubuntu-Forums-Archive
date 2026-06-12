---
title: "bus error when trying to run apt-get, synaptic or aptitude"
date: 2007-01-27
forum: General Help
---

### Post by ok67 on 2007-01-27
If I try to run either synaptic, apt-get or aptitude I end up with a bus-error message (and core dumped).

This did happened after I installed Beryl, don't know if it is the Beryl installation that is causing this. I am not using Beryl at the moment, just the plain old Gnome.
I can not remove Beryl either, since apt-get does not work, nor can I check for new software to update anything. 

I did install some updates today with the update manager, and that was after I installed Beryl, this might indicate that it is not Beryl that is the source of the problem, but rather the packages that was updated today.

I do not want to reinstall the entire system, any suggestions ?

---

### Post by ok67 on 2007-01-27
**Problem solved.**
There was something wrong with one of the files in ***/var/cache/apt/***
I just moved the two *.bin files to a backup directory and then everything was OK.

---

