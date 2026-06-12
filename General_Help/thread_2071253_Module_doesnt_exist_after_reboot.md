---
title: "Module doesnt exist after reboot?"
date: 2012-10-14
forum: General Help
---

### Post by xavieranderson on 2012-10-14
I have Ubuntu 64bit 12.04 

I had successfully installed ndiswrapper, and my wireless adapter driver. I installed system updates, restarted and then my drivers were no where to be found.

When I did the following...

> sudo modprobe ndiswrapper

I had no results returned. 

So I continued my search.

> xavier@xavier-ubuntu:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
xavier@xavier-ubuntu:~/Desktop$ loadndisdriver-1.9
xavier@xavier-ubuntu:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
xavier@xavier-ubuntu:~/Desktop$ loadndisdriver
xavier@xavier-ubuntu:~/Desktop$ loadndisdrive
No command 'loadndisdrive' found, did you mean:
 Command 'loadndisdriver' from package 'ndiswrapper-common' (main)
loadndisdrive: command not found
xavier@xavier-ubuntu:~/Desktop$ loadndisdriver
xavier@xavier-ubuntu:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
xavier@xavier-ubuntu:~/Desktop$ 


I also do not have an ethernet connection. I need to fix this, as I have no internet now. :(

---

