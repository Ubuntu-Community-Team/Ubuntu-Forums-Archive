---
title: "Synergy XP and Ubuntu Gutsy"
date: 2007-12-19
forum: General Help
---

### Post by basjava on 2007-12-19
I was able to install Synergy on Ubuntu Gutsy and my Windows XP machine. I am running the XP machine as the server and Ubuntu as the client. Both the mouse and keyboard work perfectly, when they work. About every 1-5 minutes the connection will just end and a little while later (usually less than a minute) it will connect again. Both machines are on a 100mb connection. Both are versions 1.3.1.

heres a little excerpt from the server's log.
Main is the server, Dell is the client

```
INFO: switch from "Main" to "Dell" at 1023,7
INFO: leaving screen
INFO: switch from "Dell" to "Main" at 3,151
INFO: entering screen
NOTE: client "Dell" is dead
NOTE: accepted client connection
NOTE: error communicating with new client
NOTE: accepted client connection
NOTE: error communicating with new client
NOTE: accepted client connection
NOTE: client "Dell" has connected
INFO: switch from "Main" to "Dell" at 1023,299
INFO: leaving screen
```

Any help would be appreciated.

---

### Post by Phurious on 2007-12-19
My first thought - XP firewall issue?  Have you tried reversing the machines' roles?

---

### Post by basjava on 2007-12-19
Thank you for the reply. I was finally able to get the server setup on Ubuntu and the XP machine connected, however it is still randomly failing and reconnecting. I was already allowing 24800 through both UDP and TCP, but I also turned it off just in case.

---

### Post by basjava on 2007-12-22
Update:

I am currently dual booting both of my machines with XP pro and Gutsy, so I decided to switch roles and try to isolate it to one of the operating systems. The problem still occurs when using XP on both machines, but very infrequently. Usually it would disconnect once every 20-30 minutes. When using my laptop as XP and my desktop as Gutsy (which is opposite of my original setup), I still get random disconnects just as frequently as before.

I also tried changing the priority of the synergyc process to -20, with no luck.

Does anyone have any suggestions? :?:

---

