---
title: "log of and restart x server problem"
date: 2008-01-31
forum: General Help
---

### Post by DamagePlan on 2008-01-31
Hey, I have already posted a help thread on this in another section but I didn't get any replies and hope to in this thread :) The problem I am having is when I restart the x server or log of my computer, my computer just crashes and I am left with just the desktop picture and nothing else. I can shut down but nothing else.

Any ideas?

Thanks :)

---

### Post by prince_niceguy on 2008-01-31
there should be xsession-errors file in your home directory, they should give some clue.

Also, post the xorg.log in /var/log, they will contain errors in xserver if any.

are you using compiz? if yes, try disabling it and see if it is working.

---

