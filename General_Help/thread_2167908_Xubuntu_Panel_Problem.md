---
title: "Xubuntu Panel Problem"
date: 2013-08-15
forum: General Help
---

### Post by jp42simm on 2013-08-15
Hi to everyone.   I like Ubuntu mainly because of the expanded software options that other Linux flavors do not provide but do not care for Unity, Kubuntu, Mate, Cinnamon and especially Kubuntu desktops because of their large and unwieldy menus.   I prefer the older (Debian) style where a menu simply drops from the upper left showing all the options all at once.   Xubuntu is the only version of Ubuntu which allows what I like in menus so here I am trying to use Xubuntu 13.04.   But, oops......   there is a problem.    I don't like the panel at the bottom which pops up all the time obscuring the lower part of the screen and tried to disable it to no avail.   What happened was that I accidently deleted the panel at the top which provides all the essential icons for menu, network, volume and all that other stuff.   On the panel preferences there is no differentiation between the panel at the top and the large one that pops up at the bottom.  All the panels are simply numbered without indicating which is which so I deleted them all not realizing that the top strip was also called a "panel".  Now, after, clicking around trying to fix it I have one blank panel labeled panel 3 but no panel 1 or 2 and the small panel that is supposed to be at the top is gone.   Instead of removing the popping panel at the bottom I messed the whole desktop up royally.   I blame this on grossly inadequate panel information, instructions and options.   What I would like to do is two things.   First to restore the original desktop and second get rid, permanently, of the popping panel (which is quite unnecessary) at the bottom.   Hopefully I don't have to get buried in a terminal to do this.   Isn't there an easy way to do what I want?   I am not new to Xubuntu.   I've used it for years and years and know well enough that it's desktop options are not as elegant as other, heavier, versions but it'd be nice if I could simply restore the default desktop.   Can't this be done?

Thanks to everyone for taking to trouble to read this far.

---

### Post by chk1827 on 2013-08-15
In the third panel, you could right click, then -> Panel Preferences. From Here you can click on the + button to bring up panels 1 and 2. Note that their functioality may not return; so right click on panel 1->Panel->Add New Items and add the following- Applications Menu, Clock, Seperator, Window Buttons, Workspace Switcher, Notification Area, Action Buttons, Show Desktop....This would give you a working panel..those are my options,and  you could modify them any way you want.!

---

### Post by jp42simm on 2013-08-15
Doesn't work.   Clicking "new" from the third panel creates more panels beginning with "four then five then six".   Panels "one and two" are gone.   It is worth noting here that panel "one" was unique in design, the panel at the top.   All other panels are the type that appear and behave like the poping panel at the bottom which I detest.

---

### Post by ajgreeny on 2013-08-15
Not sure about this but try renaming the hidden folder **~/.config/xfce4/panel/** in your home as a backup and then logout and in again.  I think your panels should now have reverted to the default that you had at installation and you can try again to remove the panel2 by right clicking in it when your cursor makes it pop up and using the **Panel ->Panel Preferences** dialog.  You can easily check that you have the correct panel by looking at the Items tab which should show mainly launchers in that pop-up panel.

---

### Post by chk1827 on 2013-08-15
I think you can change the popping nature of the panels by enabling or disabling AutoHide

---

