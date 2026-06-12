---
title: "Lock To Launcher Works As Admin But Not As Standard User"
date: 2015-06-30
forum: General Help
---

### Post by Tech0 on 2015-06-30
Ubuntu 14.04.2 32bit.
User 1 = Admin
User 2 = Standard

When I log-in as the admin I can lock programs to the launcher (side  bar) without any problems. But when I log-in as the standard user I can  lock some programs to the launcher but not all.

Any advice?

---

### Post by Tech0 on 2015-07-01
Problem fixed.

The program in question (jaaa) uses 2 launcher  icons, I guess one is a main icon and the other is an active icon that  only shows up when the program is running.
When I installed jaaa to the admin account, the main icon showed on the launcher and I could lock it.
When  I switched to the standard user account, the jaaa icon was not listed  and running the program only showed the active icon which cannot be  locked to the launcher.
Doing a command line <locate  jaaa-alsa.desktop> showed me where the desktop file was and I just  click-drag the file onto the launcher and locked it.

---

