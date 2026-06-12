---
title: "Multiple Installations"
date: 2007-11-26
forum: General Help
---

### Post by andthereitgoes on 2007-11-26
Hi
i have 3 machines and a laptop all running ubuntu.
i have just recently made the switch.

i would like to know, how can i install software on all the 3 machines and laptop
simultaneously. ( remotely? and at the same time interval ) 

A

---

### Post by daengbo on 2007-11-26
A program called multissh can do what you want. You just ssh into several machines simultaneously and execute a 'sudo aptitude install foo' command.

It doesn't appear to be in the repos, but clusterssh appears to be similar. Install SSH on all machines, set them up to respect keys, and you should be golden.

---

