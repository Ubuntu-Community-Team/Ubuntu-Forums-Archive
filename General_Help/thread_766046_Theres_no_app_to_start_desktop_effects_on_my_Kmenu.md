---
title: "Theres no app to start desktop effects on my Kmenu - 8.04"
date: 2008-04-25
forum: General Help
---

### Post by fabiomb on 2008-04-25
Theres no app to start desktop effects on my Kmenu, simply i need the link/route to launch the app.:mad:

I have an upgraded Kubuntu, from 7.10 to 8.04, and after the upgrade i can't find the option on my KMenu

I know, it's a very stupid question, but i can't find it searching on the forum because in every doc everybody says "Kmenu-Settings-Desktop Effects" and that entry doesn't exist here.

Maybe it's a bug in my spanish-translated version (i don't think so) or a problem with upgraded versions with kubuntu-desktop and ubuntu-desktop (probably) on the same install, i don't know, i must research...

so, someone has the link? it's a simple search on the menu editor :D :)

thanks for the little help ;)

---

### Post by kower on 2008-04-25
sudo apt-get install compizconfig-settings-manager

If you don't want to install full manager you can select one of three options in display properies, sth like compiz off, lite and full. Sorry of being imprecise, but I can't check it precisely.
Hope it will help.
Greetings.

---

### Post by fabiomb on 2008-04-25
> **kower said:**
> sudo apt-get install compizconfig-settings-manager

If you don't want to install full manager you can select one of three options in display properies, sth like compiz off, lite and full. Sorry of being imprecise, but I can't check it precisely.
Hope it will help.
Greetings.

thanks, but i have yet the complete manager, the problem is i haven't in the display properties the new "simple" manager to "start" Compiz (yes, i can do it from my terminal, but i want to let my family use this feature, not opening a konsole)

i only need to know wich app starts in Kmenu->Settings->Desktop Effects :(

---

### Post by curtis1552 on 2008-04-30
I'm usung KDE 3.5
it's not under settings, it's under system.
K > System > Desktop Effects.

---

### Post by Zorael on 2008-05-01
I'll just barge in and recommend that you install **fusion-icon** (package of the same name), and use it to start Compiz. To make it load on login, place a symbolic link to it in your autostart folder.
```
$ ln -s /usr/bin/fusion-icon ~/.kde/Autostart/fusion-icon
```

---

