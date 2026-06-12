---
title: "Ubuntu Recently Started Slowing Down"
date: 2015-09-02
forum: General Help
---

### Post by ndstate on 2015-09-02
Hello,

In the past few weeks Ubuntu 14.04 (64bit) has significantly started slowing down. I am using a Lenovo y580. The specs: 2.3GHz Intel Core i7-3610QM processor, 8GB RAM, 2GB Nvidia GeForce GTX660M GPU, 512 GB SSD. The computer locks up using Firefox with one tab open. It cannot handle Opera or Chromium with more than 5 tabs open. CPU skyrockets, ram skyrockets, etc. I use to be able to run Firefox with over 100 tabs open while also playing music with Rhythmbox, transferring files, and running other programs.

How can I begin to figure this out?

Thanks you.

---

### Post by Double.J on 2015-09-02
Hi there,

That is very strange, and I'm sure frustrating!!

Generally first step is start bug fixing is identify the fault so it can be reproduced:
-which software is directly affected; Is this only happening with internet browsers, or all tasks?
-When the resource usage spikes, which process is hogging all the activity in system monitor?
-if you start an affected program from the command line, does it give you any error messages that may explain what is happening? (Do not use root privilages)
These tell you a bit more about the fault and how to reproduce it, then we try and narrow where it is:
-Does the issue happen if you log in as a new user?
This can tell you if the problem is going to be in your home folder rather than the packages themselves - no point removing and reinstalling packages if the problem is in config files! It doesn't rule out system wide settings however.
-Does the fault persist if the package is reinstalled? 
This should narrow the fault to system wide config files and dependencies. Configs can usually be identified just by changing their name to see if their absence solves the problem, dependencies can get a bit more tricky, but If you've managed to narrow the fault to a specific package or set of packages, purging them then reinstalling can shorten the process.

Sorry it's all a bit vague, but at the moment we really don't know much about what's going on, so these would be the steps I would take.

Best of luck,

JJ

---

