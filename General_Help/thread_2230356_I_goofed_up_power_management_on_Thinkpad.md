---
title: "I goofed up power management on Thinkpad"
date: 2014-06-18
forum: General Help
---

### Post by cpdondo on 2014-06-18
I tried to get hibernation working on my Thinkpad W530 when I close the lid.

I enabled hibernation and did some testing.

It didn't work; eventhough pm-hibernate would would hibernate the laptop would freeze on restart.  
I changed /etc/systemd/logind.conf to 

HandleLidSwitch=poweroff

to try to get it to shutdown.  I must have done something else too because now the system ignores the settings in logind.conf.  It basically goes into a low-power state, with the screen off when I shut the lid.

Where do I look?  I have no idea what I've done...

---

