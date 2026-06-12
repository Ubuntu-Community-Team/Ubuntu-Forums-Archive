---
title: "NUC5i7RYH screen goes black and doesn't come back"
date: 2016-04-05
forum: General Help
---

### Post by Chuck_McManis on 2016-04-05
Running 15.10 on an Intel NUC5i7RYH with the IRIS graphics 6100. All patched and up to date.

After an extended period of idleness (usually overnight) the screen is off an dark, but nothing will "wake up" the system (it isn't really asleep, I can ssh into it from another machine) and if I use CTRL-ALT-F3 to pull up an alternate console that works fine. But I can't get the window system back. If I kill off [FONT=system]/bin/sddm[/FONT] manually (the child running my X session) then the the login manager returns and I can log in again and I'm back. Of course that kills off things like my terminal sessions and other windows which is annoying. 

So the simple question, how can I figure out what that process is doing which is preventing it from "waking up" and putting the login screen up? 

--Chuck

---

