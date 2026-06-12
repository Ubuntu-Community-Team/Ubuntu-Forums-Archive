---
title: "Failed Journal Service"
date: 2019-12-26
forum: General Help
---

### Post by zkab on 2019-12-26
I have Ubuntu 18.04 LTS and in the middle of nothing my system behaved strange ... man command didn't work and so on ...
I made a reboot and got output from Grub 2.02

Ubuntu
Advanced options for Ubuntu
System setup

I chose first option and got error 'Failed to start Journal Service' ...  
After that the system continued to print a lot of messages ... don't know how to get a logfile so I attached a photo.

How can I save my system or is it lost?

---

### Post by zkab on 2019-12-27
OK ... I managed to get the command prompt from Grub
When I gave the command (as suggested  in error message): 'systemctl status systemd-journald.service'
I got following: 'System has not been booted with systemd as init system (PID 1). Can't operate'

Anyone ? I can't the first one in Ubuntu community that encountered this ...

---

