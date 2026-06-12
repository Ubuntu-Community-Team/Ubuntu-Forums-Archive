---
title: "Cannot log-in ... Help !!!"
date: 2013-06-09
forum: General Help
---

### Post by jfl on 2013-06-09
I was trying to fix a bottom panel problem, ran "Tweaks" and now I cannot log-in. 

[COLOR="#008080"]I get to the login window, select my account, enter my pw, screen goes dark for a few seconds and I am back at the log-in window   !!!
If I select the "Guest" account, it works fine.
[/COLOR]
I do not get the red "Invalid password"; I know the pw is correct (used passwd in terminal).

I can log-in as a guest, so I created another Admin account but it would be a major PITA to recreate the original one.

Any ideas are welcome !!!

---

### Post by steeldriver on 2013-06-09
It sounds like your X session is unable to start for some reason - that may be something you tweaked, or (depending on how you ran the Tweaks program) it may be that your session file ownership/permissions got screwed up - first thing to check would be your home folder and Xauthority file:

```

ls -ld $HOME

ls -l $HOME/.Xauthority

```

---

### Post by jfl on 2013-06-09
Yep, Thanks !!!
.Xauthority was owned by root and not by me; it just took a chown.
Appreciate it.

---

