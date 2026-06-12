---
title: "System load increases for no obvious reason until system crashes"
date: 2015-10-22
forum: General Help
---

### Post by AllesMeins on 2015-10-22
Hi,

in the last weeks I'd some strange problems with my system. For nor obvious reason the average load (as reported by uptime) starts to increase suddenly. Than it just keeps rising and rising, up to values of 50 or 60 and than the system crashes. CPU-Usage (under 10%) and Disc Access are all looking fine, RAM is filled to about 70 % - so something other must be blocking my system. But I've no idea how to figure out what it might be. Can anybody help me how to find the problem?

Wild speculation: Maybe firefox is part of the problems. Often a non responsive firefox is the first sign of trouble. When trying to kill it, the process stays as "<defunct>" in the list. Other possible explanation: I've a NFS connected to my media server on my system and I've read that sometimes those mounts might cause problems. But as I said - these are just guesses. I haven't been able to pin it on one or the other, because the problem appears irregular.

My System:

Ubuntu 14.04
Kernel: 3.13.0-67-generic
Core i7-3770
8 GB RAM

---

### Post by ajgreeny on 2015-10-22
When the system next starts to run slowly open a terminal and use command **top** which will list the processes in use.  Now press an upper-case C to sort the list by CPU%, or upper-case M to sort by memory use, and you may get some clues about the culprit.

---

