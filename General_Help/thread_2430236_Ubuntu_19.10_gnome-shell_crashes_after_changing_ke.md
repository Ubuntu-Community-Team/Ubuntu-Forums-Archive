---
title: "Ubuntu 19.10 gnome-shell crashes after changing keyboard"
date: 2019-10-29
forum: General Help
---

### Post by fubukist on 2019-10-29
Updated to Ubuntu 19.10 Eoan, changing keyboard (from zh-cn to es-es)  crashes gnome-shell, and displays that logoff is needed, but clicking  logoff button is useless (won't work). Reboot, log in, and a black  screen with movable cursur will be displayed. After some time, the crash  screen will again be displayed.
  Checked journalctl /usr/bin/gnome-shell, a lot of (about 10-50 lines per second) gnome-shell[1907]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed was found.

  Use tty3 to login and deleting ~/.config/dconf/user  would help logging in to desktop environment (gnome won't display dock,  and have no settings of dock for some reason though), but changing  keyboard still crashes gnome as before.
  I tried adding disco and focal apt source into sources.list, and use  aptitude to upgrade, or downgrade gnome to other versions. Things won't  work either (can't even login).

  After some googling, I found a possibly related PR: [https://gitlab.gnome.org/GNOME/mutter/merge_requests/764](https://gitlab.gnome.org/GNOME/mutter/merge_requests/764), but this commit is on 3.35.1, not 3.34.

  Is there any ways to use that patch without compiling it myself, or  if there are any workarounds that can solve the problem (e.g. rollback)?  
I might consider changing to unity or kde for some time though...
Thanks for your help!

---

