---
title: "Font sizing problem"
date: 2007-04-03
forum: General Help
---

### Post by razorfrog on 2007-04-03
I recently installed ubuntu 6.10 and am having issues with font sizes. The default application font (specifically what firefox uses for menus, tabs, etc, is strangely bold and large - yet the ubuntu settings do not affect it.. How can I shrink the fontsize? 

I attached a screenshot, you can see what I'm talking about.

Thanks!

[IMG]http://razorfrog.com/images/fonts.png[/IMG]

---

### Post by amohanty on 2007-04-03
You seem to be running beryl.
Open up a terminal and run:
gnome-settings-daemon
If that works add that to your session via:
System->Preferences->Sessions->Startup Programs

HTH
AM

---

### Post by razorfrog on 2007-04-03
wow. that made the terminal basically throw up.. but it worked!  thanks so much..
just for my learning and future reference.. what was that? what did it do?

---

### Post by amohanty on 2007-04-03
when you use the System->Preferences->... to setup how the desktop looks and behaves, the settings are stored in  a whole bunch of files in ~/.gconfd and ~/.gnome

These are loaded up and managed by this daemon. Well its a bit more complex than that, but thats the short answer.

Also mentioned here:
[http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl#Cannot_use_hotkey](http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl#Cannot_use_hotkey)

HTH
AM

---

