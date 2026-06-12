---
title: "Many identical Processes in shown on TOP"
date: 2013-01-02
forum: General Help
---

### Post by misterfixit on 2013-01-02
When using Totem to preview videos, I open and close it many times.  I see from my process table that there are at least 10 totem proccesses.  Also a whole lot of xfce4-notiyd processes.  I "thought" that a parent process was supposed to issue a WAIT4() call and terminate when the process ends.  Totem and xfce4-notifyd seem to not be responding to the termination.  Could this be because the process is failing to issue a CALL WAIT4() and totem ( and others) are not issuing the process end signal?  I have loads of RAM but still, the appearance of totem running some 1.2MB of RAM (at 10K per instance) is bothersome to my orderly mind.

I would appreciate comments .. and especially guidance of any errors of thoughts on my part.

---

