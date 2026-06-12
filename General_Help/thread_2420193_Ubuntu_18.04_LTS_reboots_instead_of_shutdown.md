---
title: "Ubuntu 18.04 LTS reboots instead of shutdown"
date: 2019-05-31
forum: General Help
---

### Post by halfhogshead on 2019-05-31
Installed Ubuntu 18.04 LTS server on Asrock Desk mini 310 and apt update / apt upgrade the system one month ago. Everything worked fine until May 29th, when I updated the system: the computer cannot be shut down. Every time I run "sudo shutdown -h now" the machine shuts down but restarts after a couple of seconds. 

I have tried to shut down from GUI, or use "sudo shutdown -P now" or use systemctl to power off the machine. I have also disabled Wake-on-LAN, disabled wifi altogether from BIOS, unplugged the LAN cable, but the computer keeps rebooting afterward. 

It seems to me a recent update in 18.04LTS caused the problem. Any ideas? Thanks a lot!

---

### Post by cruzer001 on 2019-06-01
A long shot, but could it be a kernel regression?

Try dropping back to previous kernel.

---

