---
title: "Not enough freee disk space to do an update."
date: 2014-07-18
forum: General Help
---

### Post by castlefox on 2014-07-18
I am using Xubuntu 14.04

When I try to do an update it says 

"Not enough free disk space"

"The upgrdade needs a total of 78.7 free space on disk '/book'. Please free at least an addiitonal 5,570k of disk pace on '/boot'. Empty your trash and remove temporary packages from former installations using 'sudo apt-get clean'.



I dont know how to make more addition space on /boot.    I already emptyed my trash and this was a fresh install but I did the 'sudo apt-get clean' but that apparnetly didd nothing b/c & it didnt seem to fix anything.  

Please advise.  Thanks !

---

### Post by Bucky Ball on 2014-07-18
You say update, the machine says upgrade. Are you attempting to upgrade to a newer release?

Either way, run:

```
sudo apt-get clean
sudo apt-get autoclean
```

Careful emptying boot. Best is to open a terminal and:

uname -r

Take note of the kernel you are using. Open Synaptics and search for 'linux image'. Delete all but the one you're using and the one prior to that (if you are using -32 for instance, keep -31 also and kill the rest).

---

### Post by castlefox on 2014-07-19
I said 'update'  because I was using the "Software Udpate" and I was not up grading to 14.10 or something like that.... 

Anyways I restarted my PC and then I was able to do all of the updates that the software updater found.... so... idk what I did but its magically working now.

---

### Post by Bucky Ball on 2014-07-20
Good news. Must have been the incantations, dancing in a circle and throwing a pinch of salt over the shoulder that did it! In the absence of a 'resolved' option, please mark thread a solved to help others. Good luck. ;)

---

### Post by castlefox on 2014-07-20
How do I mark this as solved ?

---

### Post by Bashing-om on 2014-07-20
castlefox; Hi !

To mark as solved -> top of thread -> thread tools:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

