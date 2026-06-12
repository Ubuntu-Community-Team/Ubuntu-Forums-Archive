---
title: "Startup Applications, not starting at startup"
date: 2015-07-19
forum: General Help
---

### Post by anthony71 on 2015-07-19
Hello

I've added xscreensaver to the startup applications list but it does not start. If I run the .desktop it works fine.

I've been looking for answers for a while and nothing I've found works, Please help its driving me mad!

---

### Post by ian-weisser on 2015-07-19
Are you saying that you want to login to your system and see the screensaver first instead of your desktop?

---

### Post by anthony71 on 2015-07-19
No, I want the screensaver to start on boot rather than having to run it manually each time

---

### Post by deadflowr on 2015-07-19
Perhaps it's because gnome-screensaver is starting with a delay.
Which is overriding the xscreensaver settings.
This assumes you are running regular Ubuntu.

All my gnome-screensaver autostart .desktop files in
*/etc/xdg/autostart*
contain this line
[I]X-GNOME-Autostart-Delay=20
[/I]
(The 20 equals seconds which equates to when you initiate logging in.
Without the delay a startup .desktop files action could occur at anytime after you press enter to login. Be it immediately upon login or 10 seconds)

Just a thought.
Could be completely wrong...

---

### Post by anthony71 on 2015-07-19
Hi deadflowr, I tried removing the gnome-screensaver .desktop files and nothing changed. I thought that wasnt running anyway

---

### Post by Dennis N on 2015-07-19
To get xscreensaver working in Ubuntu, I do the following:

1. uncheck gnome-screensaver in the startup applications list. In the list, it is called 'Screensaver' - you don't have to uninstall it. 
2. add xscreensaver as a separate new entry to this list and mark its checkbox. Command: **xscreensaver -no-splash**

Configure:
Search for screensaver in Dash to set your preferences. This starts the GUI setup dialog.
Note:
xscreensaver has only a few screensavers. You should also install:
xscreensaver-data-extra
xscreensaver-gl
xscreensavergl-extra
rss-glx
to have a full selection.

To get rss-glx screensavers to work, see /usr/share/doc/rss-glx/README.xscreensaver

Reference system: Ubuntu 12.04

---

### Post by anthony71 on 2015-07-20
Thanks for all you help, it was the -no-splash that finally fixed it

---

