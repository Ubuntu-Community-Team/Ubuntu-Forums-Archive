---
title: "Can't get xscreensaver daemon to start"
date: 2008-07-09
forum: General Help
---

### Post by phatchow on 2008-07-09
It starts from the command line without issue.  Have read xscreensaver man page and faq.

I'm using Hardy Server edition using xdm and icewm.  I would like to get xscreensaver to run for all users, but would settle for getting to run on a per user basis.

If I put the line

xscreensaver -nosplash & 

in ~/.xsession, I get kicked back to the login prompt.  .xsession-errors says:

xscreensaver: Can't open display: :0

tried the same thing in ~/.xinitrc, this apparently does not get executed unless you start X with xinit vice xdm.

Have also tried various places at the system level like /etc/x11/xinit/xinitrc, no dice.

So, where is the correct place to put this so the daemon gets started.  Any help would be greatly appreciated.

---

### Post by john.nicholls on 2008-07-10
I start it with ```
xscreensaver-demo
```

---

### Post by phatchow on 2008-07-10
When you run xscreensaver-demo, if the daemon (called 'xscreensaver') isn't already running, the demo will ask you if you want to start it.  I would like the daemon to run when one logs in.

---

