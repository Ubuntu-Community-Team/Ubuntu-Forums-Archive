---
title: "XGL Keyboard Layout Problem"
date: 2006-11-23
forum: General Help
---

### Post by nb_alexiev on 2006-11-23
Hello guys, I'm new to Ubuntu, but I'm really happy with it and the support from the community.
Unfortunately I'm hitting the wall at the moment ](*,).

I use Ubuntu Edgy 6.10 on Acer Aspire 5021 with Turion 64 and ATI x750.

I installed XGL/Beryl and everything was OK till yesterday.
When I logged the XGL session it asked if I want to keep my GNOME keyboard settings or to use another one (I think it was xkeyboard or something like that). I choosed the second one because key combitions like alt+shift weren't working.
After that I lost my layouts. I have only USA and ?,?2 for the others.
After one day reading and testing I have the following situation keyboard layouts working in all sessions except XGL. 

When i start #gnome-settings-daemon in XGL the layouts start working but only for the current session when I log out and in again, the situation is the same. It gives the following message "![1164308293,000,xklavier_evt_xkb.c: xkl_xkb_process_x_event/]   ATTENTION! Currently cached group 0 is not equal to the current group from the event: 1" + many Warnings for undifine symbols.

I tried #sudo gnome-settings-daemon but it crashes with a bug. The report is attached.

I'm totally lost and I can't find a method for permanent solutions.

XGL is started through a startup script only for XGL session.

Thank you for the help in advance.

---

### Post by FenrisAbraxas on 2006-12-30
Check:

[This post!]("http://ubuntuforums.org/showthread.php?p=1946677#post1946677")

---

