---
title: "Lock screen bugged after resume from standby"
date: 2016-01-27
forum: General Help
---

### Post by ReFike on 2016-01-27
I have Kubuntu 15.04 on a laptop. Resumed from standby today but my lock  screen bugged, only thing I have is the mouse pointer and I can barely  see the wallpaper and all my open applications in a semi transparent way  on each other, like a graphical glitch.
If I change to other terminal (ctr+alt+f1) I can login and apps seems running. 
How  can I reset this lock screen from terminal? I want to avoid a hard  shutdown because I have unsaved documents in the session. :/

---

### Post by ReFike on 2016-01-27
this did the trick
> sudo loginctl unlock-session 1

---

