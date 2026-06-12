---
title: "problems using xsane with networked scanner"
date: 2008-01-10
forum: General Help
---

### Post by donkyhotay on 2008-01-10
I recently managed to host my scanner over my personal network by using saned and xinetd. My scanner is plugged into my headless ubuntu server which is networked into my regular ubuntu desktop. Although I am able to successfully scan images with xsane on my desktop, whenever I attempt to change any settings xsane reports "Failed to set value of option mode: Invalid argument" and doesn't actually change the setting (specifically for changing from gray to color scanning). If I plug my scanner into my desktop xsane will allow me to change settings and even save them so that when I plug my scanner back into my server it will work with those settings, but of course to change settings I have to swap the scanner around which defeats the purpose of having it networked in the first place.

edit: I just found out as a workaround if I go into preferences first and don't do anything it will then let me change the settings without any problem.

---

### Post by SumnerBoy on 2008-02-24
Hi - I am trying to get my Canon MP530 scanner working but am not quite sure where to start. I have plugged it into my headless Ubuntu 7.10 Server and have managed to configure printing via CUPS and Samba (so I can print from my networked Vista laptop).

How do I go about configuring the server so I can scan from my Vista laptop as well? 

Thanks in advance,
Ben

---

