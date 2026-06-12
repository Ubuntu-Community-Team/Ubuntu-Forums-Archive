---
title: "Unable to login (wrong login screen)"
date: 2008-03-07
forum: General Help
---

### Post by beast.dk on 2008-03-07
Hi

I tried to get a login screen that would show faces and messed a bit around. In this attemp I have changed the "Launch" option under the security tab in gdmsetup to chooser. (the above is translated from Danish so I am not absolutely sure what the fields are named in English)

This means that I am now unable to see the Gnome GUI anymore. When I boot the system I see a dialog where it search for remote server for in what I belive is some sort of XDMCP remote login system. It is unable to find any servers and I am unable to login locally. I can CTRL+ALT+F1 to the command line but I am unable to start the normal xserver. Have tried to kill the process and start X again but I always ends up with the stupid dialog.

I have looked over the gdm.conf file to see what the changes might be and compared it to what I can find on the web with no luck. I have tried to issue the command "dpkg-reconfigure gdm" and some other stuff......
It now seams to me that the option is located somewhere else?

PLEASE HELP - how do I get the normal login screen back?

---

### Post by beast.dk on 2008-03-07
Nobody :confused:

---

### Post by beast.dk on 2008-03-07
Have found a thread that show the same problem. Will try some of the hints.

[http://ubuntuforums.org/showthread.php?t=703313](http://ubuntuforums.org/showthread.php?t=703313)

---

### Post by beast.dk on 2008-03-07
The last solution in the referenced thread by marcvilleneuve work e.g

In file /etc/gdm/gdm.conf-custom, find this section
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
#MVchooser=true
#MVhandled=true
flexible=true
#MVpriority=0

and comment out the lines chooser=true, handled=true and priority=0

Restart ubuntu and select the normal way to start it.

---

