---
title: "X server just keeps crashing!!"
date: 2007-07-02
forum: General Help
---

### Post by Jordan777 on 2007-07-02
Ok, please i really need help with this problem.  I've had to reinstall Ubuntu like 10 times in the past 3 days.  My X server just keeps crashing.  The first time I set up Ubuntu like last week I used Envy and I believe the restricted drivers and everything was working great.  Then I installed the new upgrades and the X server crashed.  This is where things have gone down hill.  When I reinstall I can't use any drivers that I know of without crashing the X server.  I can't even find envy in add and remove apps anymore.  Is there anything I can do?  The default X server crap drivers make me run in 1024x768 when i need to be in 1280x1024 (it looks kinda blurry and crappy otherwise) and my web browsing is really sluggish due to bad drivers.  Please I have tried to do many things that I've seen on here but hardly any work.  I haven't even tried gaming again because I don't want to see how bad the performance hit is with terrible drivers.  Is there anything I can do?  If not I may just not use Ubuntu for a while until this hopefully gets worked out. :(

---

### Post by Yettie on 2007-07-02
Can't help, only sympathise I'm afraid. I'm having problems with the system crashing since the last update.

---

### Post by Jordan777 on 2007-07-02
So do we have just have to sit back and deal with it?:(

---

### Post by geraldm on 2007-07-02
When the X server crashes you should be looking at the counsel screen with
a message stating where the log file is.  Mine were in /usr/X11R6/var/log
for the X startup log, and another in the home directory ~/.xsession-errors
There should be enough information in these to identify the problem.
The directory locathon may be /usr/X11R7/.. 

regards,
Gerald

---

