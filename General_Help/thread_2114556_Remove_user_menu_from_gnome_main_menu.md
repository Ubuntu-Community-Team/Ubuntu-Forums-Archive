---
title: "Remove user menu from gnome main menu?"
date: 2013-02-10
forum: General Help
---

### Post by darthpenguin on 2013-02-10
Hello.

I am using Ubuntu 12.10 in gnome-classic mode. I have been giving Unity a chance but it just doesn't work for me. I am tweaking my desktop to look very much like Apple's OS X (see attached screenshot). I like the gnome main menu but I don't use an instant messenger app. So I have no need for the IM status menu in the main menu. How can I remove that menu item?

Thank

---

### Post by Bufeu on 2013-02-10
Disabling the guest session will remove the user menu in Unity. [http://www.howtogeek.com/117994/how-to-disable-ubuntus-guest-session-account/](http://www.howtogeek.com/117994/how-to-disable-ubuntus-guest-session-account/) (use gksudo instead of gksu)
However, I don't know if it works if you have an other DE.

---

### Post by darthpenguin on 2013-02-10
My apologies if I was unclear. I don't care about the 'Switch User' option. This is a valid function that should be built into every operating system. I want to remove the username (blurred in screenshot) and it's pop-out menu that shows 'Available' and 'Busy'. There is no need to build this into the OS. Instant Messenger status should be controlled directly by the IM client (whatever one the user chooses to install) if the user chooses to use one at all. SMS/Smart phones and browser-based chat has all but replaced desktop IM. If it was ever necessary to integrate an IM into an OS (and it never was) it is far too late to do it now. Somebody wasted their time incorporating this stunningly useless feature and they are wasting my time trying to get rid of it.

---

### Post by ibjsb4 on 2013-02-10
I think if you do not use indicator-applet-complete that will give you the results your looking for.

[ATTACH]231246[/ATTACH]

---

### Post by darthpenguin on 2013-02-10
Thank you for your reply. However, this will not work. The User Menu is not an indicator applet nor part of the indicator-applet-complete package. The User Menu manages online status among other things and can be added to the panel as a separate applet. It is also integrated into the Main Menu applet (but not the Menu Bar which has the 'Applications' and 'Places' menu). If I could remove (uninstall) the User Menu applet perhaps it would not appear in the Main Menu. But I can't find the User Menu package to remove it. Even if I could remove it I'd loose 'Switch User', 'Log out', 'Lock Screen', and 'Power off'. Which would suck because I need these features. I have no idea why these features are in a 'User Menu' and not a 'System Menu'. Of course that is all moot as I am suspecting that this menu is built into the gnome-panel package which is nothing short of asinine. If I were better at programing I'd modify the source code of the gnome-panel to purge the online status control functions but I wouldn't know where to begin. Any other suggestions?

---

