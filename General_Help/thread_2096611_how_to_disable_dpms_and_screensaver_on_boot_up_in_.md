---
title: "how to disable dpms and screensaver on boot up in Ubuntu 12.10"
date: 2012-12-20
forum: General Help
---

### Post by tnmarktx on 2012-12-20
Ok, this is driving me crazy.  I have done a lot of research and cannot resolve this issue, and it should be very simple.
I want to disable the screensave and dpms on boot up.  I know the commands to do this, but can't figure out the file to modify that will accomplish this task.  I know that xset s off disables the screen saver and xset -dpms disables dpms.  However, no matter what I try, xset -q always shows that the screen saver is still enabled and that dpms is also enabled.

---

### Post by Merrattic on 2012-12-20
Put the commands in /etc/rc.local ? Sometimes you need to put them in a script that is run by rc.local as opposed to having the commands inside rc.local

---

