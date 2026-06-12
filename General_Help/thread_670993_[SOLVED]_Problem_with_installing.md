---
title: "[SOLVED] Problem with installing"
date: 2008-01-18
forum: General Help
---

### Post by Jbs63 on 2008-01-18
I know its probably going to be some silly small error but for some reason i cant use terminal or anything really to install applications via apt-get

for example:
jonathan@jonathan-laptop:~$ sudo apt-get install vlc
[sudo] password for jonathan:
Sorry, try again.
[sudo] password for jonathan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc

And trying to install nvidia drivers:
The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by KevMeistr on 2008-01-18
Have you tried going through the synaptic package manager ?

---

### Post by Jbs63 on 2008-01-18
na there was just no sources so i edited the file. for some reason on a fresh installation there was no sources. weird. Oh well. Problem solved

---

