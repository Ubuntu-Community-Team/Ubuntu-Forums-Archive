---
title: "Gnome panel replacement"
date: 2006-12-02
forum: General Help
---

### Post by thelinux_guy on 2006-12-02
I was wondering where I could find a replacement for the Gnome Panel,I dont like it and want another one besides this,can you give me a link of recomend something to me? thanks...-jason

---

### Post by d3v1ant_0n3 on 2006-12-02
What do you want the panel to do, and why do you want to get rid of the gnome panel? It's quite customisable if you play with it enough- the only thing I seriously dislike is the inability to remove the grab handles.

---

### Post by thelinux_guy on 2006-12-02
My friend runs Ubuntu and I needed to use his computer,He logged me on and then i noticed that he had a menu bar simulr to the one in Mac OS,I liked it,And now I want it for my system too,but I dont know where to find it,so I made this topic on this forum to increase my chances of finding it,I like the Gnome Panel,but i like that menu-bar thing,and i want it so....:p

---

### Post by thelinux_guy on 2006-12-02
My friend runs Ubuntu and I needed to use his computer,He logged me on and then i noticed that he had a menu bar similar to the one in Mac OS,I liked it,And now I want it for my system too,but I don't know where to find it,so I made this topic on this forum to increase my chances of finding it,I like the Gnome Panel,but i like that menu-bar thing,and i want it so....:p

---

### Post by d3v1ant_0n3 on 2006-12-02
Try any/all of these: Should be in repos.

1)Kxdocker- it's for KDE, but I believe it works in GNOME.

2) 'Starter Bar' applet for Gdesklets

3)Kooldock

4)Try the following with a standard gnome panel:

-Right click in empty space on a panel
-Click 'properties'
-Uncheck 'expand'
-Check 'autohide'
-Switch to the 'background' tab
-Click 'solid color' and turn the slider all the way to the left

Voila, dock like panel

---

### Post by thelinux_guy on 2006-12-02
is there anyway I can add menus to the Gnome Panel? I already know about the "menu bar",the "main menu",and the drawers you can add to the panel but i was wondering if i could add just menus to panels and stuff...

---

### Post by matthew on 2006-12-03
I moved this to a more appropriate forum.

---

### Post by DMBryant on 2006-12-09
I think this is probably what you are after:

[http://www.ubuntuforums.org/showthread.php?t=241868&highlight=mac+panel]("http://www.ubuntuforums.org/showthread.php?t=241868&highlight=mac+panel")

---

### Post by thelinux_guy on 2006-12-12
> **DMBryant said:**
> I think this is probably what you are after:

[http://www.ubuntuforums.org/showthread.php?t=241868&highlight=mac+panel]("http://www.ubuntuforums.org/showthread.php?t=241868&highlight=mac+panel")

yes ! thats what I was looking for,but how to install it? I read the directions,to complicated,can someone simplify it for my ?

---

### Post by mcduck on 2006-12-12
First download gnome-macmenu-applet, libgtk2.0, libgtk2.0-bin and libgtk2.0-common from here: [http://chrislord.net/files/gtkmenubar/]("http://chrislord.net/files/gtkmenubar/")

Then install them all with 'dpkg -i package1 package2' (use the real names of packages of course.

Next right-click on your panel, select 'Add to panel, find the macmenu applet and drag it to your panel.

You may need to log out and back in again before everything works.

Note, that Update Manager will want to replace those libgtk-packages with versions in Ubuntu repositories so you should lock the versions in Synaptic (select package, and then Package/Lock Version). For some reason I wasn't able to lock packages in Edgy but perhaps you can. Otherwise when getting updates just unmark those packages every time.

---

### Post by thelinux_guy on 2006-12-18
I cant seem to get it installed,I have the "mac menu" choice in my "add to panel" but it dosent have menus,I cant install through "dpkg" in terminal,what am i doing wrong?

---

### Post by thelinux_guy on 2007-01-06
Is anyone there? I have tried this many times and failed,can someone post step-by-step instructions on how to install this? I have followed the one created by Zammi on Gnome-look but that didnt work....


Someone help!

---

### Post by rosslev on 2007-01-08
I have the same problem, I have however, successfully installed the pakages from the command line as suggested (it performed a downgrade).

---

### Post by alfiejs on 2007-04-21
I first posted this in the wrong spot.  How do I make 64bit versions of the debs?  Do  i need to make them from the source files?  And how exactly would I go about doing it?

---

