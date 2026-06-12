---
title: "Ubuntu randomly restarting?"
date: 2007-12-24
forum: General Help
---

### Post by HelloGopher on 2007-12-24
Hello :) I recently installed Ubuntu on my computer and so far it has been great except for one small problem: three times now it has randomly reboot on me. It isn't that my whole computer restarts, but rather the screen will go blank, and then it will say "Starting [some process]...." for about 8 different things, and then I'll be at the login screen.

I've tried looking through the logs immediately after this happens, and now that I look back on them, I do see this little bit in daemon.log:

>  WARNING: gdm_slave_xioerror_handler: Fatal X error 
and this, at the same time, in auth.log:
> pam_unix(cron:session): session opened for user root by (uid=0)
syslog:
> WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

But nothing before that, and the stuff after is just me logging back in. I can't be sure, since it is usually so sudden, but I believe that it has happened every time I have some music playing and I click on something on the bar at the bottom. 

I have been having some problems with playing music; sometimes, if I play music for too long, suddenly I won't be able to open anything by double clicking on it (the icon will turn into a piece of paper), and the only solution is for me to go into the terminal and type "killall nautilus". 

Any help would be appreciated, since it is a somewhat distracting error. I haven't lost any important work yet, but it makes me a bit paranoid :) Thanks in advance!

---

### Post by TidusBlade on 2007-12-25
since you assume it's the music, what music player do you use?

---

