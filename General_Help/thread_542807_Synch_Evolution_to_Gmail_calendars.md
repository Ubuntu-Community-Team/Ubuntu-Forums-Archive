---
title: "Synch Evolution to Gmail calendars"
date: 2007-09-04
forum: General Help
---

### Post by basilwatson on 2007-09-04
Hi there 

Having read the wiki and followed the advice can anyone point me in the right direction 
I want evolution calendars to synch with google calendars 

OR 

Thunderbird to synch with my Pda ? 

When I try evolution it say host not resolved , like I guess its looking for a password??

thats my only guess though 

Any Ideas 

Stephen

---

### Post by dysonsphere23 on 2008-05-29
For synching evolution with google calendar I use gcaldaemon

[http://gcaldaemon.sourceforge.net/usage16.html](http://gcaldaemon.sourceforge.net/usage16.html)

follow the instructions for evolution and it should work just fine.

To get it to run at startup (and as a background service) copy the standalone-start.sh file into etc/int.d (change the permissions so it doesn't have to be run by root).  Then in terminal:

$ update-rc.d standalone-start.sh defaults

---

