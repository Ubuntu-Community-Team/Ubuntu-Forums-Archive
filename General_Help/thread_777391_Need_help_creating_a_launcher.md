---
title: "Need help creating a launcher"
date: 2008-05-01
forum: General Help
---

### Post by bgreenaway on 2008-05-01
Apologies in advance for what is probably a very simple question...

Using Ubuntu 7.10 Gutsy. I use the following command from a Gnome Terminal session to connect to one of my W2K3 servers for remote desktop session:

*rdesktop -g85% -a16 -uadministrator [server-name]*

Works fine in Terminal, but I would like to create a launcher for it for my desktop and/or panel. When I try to create a launcher and just use the above command, the result is a ridiculously narrow window, which I am unable to resize. Can anyone give me the format of the command to use for the launcher?

---

### Post by seanathanakaking on 2008-06-13
I think i'm just as new as you if not newer to ubuntu but i found this in the help thing when you don't completely enter the command right. Use the -f command to enable full screen. If you don't want full screen just enter rdesktop in the terminal and it will give you a list of the context and all the switches.

the command that worked for me was:
rdesktop -d[domain] -f -xl [server ip]

-f: full screen
-x: RDP experience l is for lan

---

