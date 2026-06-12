---
title: "No login prompt/screen after boot"
date: 2015-05-09
forum: General Help
---

### Post by andy.quint on 2015-05-09
Hello everyone!


Trying to find a solution to my problem trying to locally log into the system.


This is a home server that also serves as web server. Everything has been setup and working perfectly fine. I recently had to do an update and something broke, and all of a sudden certain services were not loading on boot, such as apache, webmin, vnc, etc. I tried to go to the box itself and hook up a monitor to it and when i booted, i got the Xubuntu splash screen and then went to a black screen with a small white cursor on the top left corner.


Long story short, everything on the server is back to normal now and all services are now running back on boot again, so that problem is fixed. However, now i am curious as to why i cannot get a login screen after boot. If i vnc from my windows laptop to the server, it works perfectly fine - getting GDM login and able to log in with no issues. 


Checking webmin under services does show that both LightDM and GDM are loaded on boot, is this normal that 2 DM's load at boot?
What could be the cause and how to fix the missing login screen after my box boots up?


I tried a few solutions i found such as ctrl+alt+f-key but this does work, it does not open a terminal. Also tried reinstall/config ubuntu desktop (this is what actually fixed my original problem above) but still no login.


any help?
Thanks!

---

