---
title: "[SOLVED] Where is the terminal?"
date: 2008-02-29
forum: General Help
---

### Post by Bruce M. on 2008-02-29
Hi Folks,

I just did a clean install of **Xubuntu 7.10**, *I'm really going to miss Gnome*, :cry: but so far this seems to be running faster and using less CPU processes (94 vs 186).

However, being NEW to **Xubuntu** I have a couple of questions:

[LIST]
[*]I can't find the Terminal program.
[/LIST]

Not totally true I do see **Xfce terminal emulator** [ with a $ in the window], however using it turns my screen black - it's larger then my screen, so I don't see everything and can't figure out how to get out of it and back to the desktop. I have to [Reset] which is NOT a nice thing to do to a system.

[LIST]
[*]Next I installed the Gnome Terminal
[/LIST]
 But can't see it anywhere in the menus. So I'll be deleting that now.


I'd really appreciate some suggestions.
Bruce

---

### Post by WarMonkey on 2008-02-29
I think you can get out of the terminal by using "exit". I haven't used xfce in a while, so I could be wrong.

---

### Post by Bruce M. on 2008-02-29
> **WarMonkey said:**
> I think you can get out of the terminal by using "exit". I haven't used xfce in a while, so I could be wrong.

I tried that, brings me right back to the terminal.

---

### Post by soldats on 2008-02-29
in the menu there *should* be 2 options for teminal it should be in applications>system>terminal. if for some reason that doesnt work try doing alt-f2 and it should bring up a "run" box and you should be able to enter the command gnome-terminal which you installed or xterm which is the basic terminal that comes with the install. for some reason the gnome-terminal didnt automatically set it self in the menu so the easiest way is to do a locate command to find the gnome-terminal executable and from there you will be able to add an entry to the /usr/share/application folder where the menu items are located. each item in the folder is a .desktop item which adds itself to the menu automatically. so try viewing a few of them and create a new .desktop file with the gnome-terminal info and it should autogenerate a menu ntry for it. but first id look in the area i suggested earlier to find the terminal. if it only shows a $ try to "su" to your user name and you should have it. maybe leave it open all the time?  if you need more assistance find my nick "soldats" on #ubuntu or #ubuntu-us-az and ill be happy to help you   :)

---

### Post by Bruce M. on 2008-02-29
> **soldats said:**
> in the menu there *should* be 2 options for teminal it should be in applications>system>terminal. if for some reason that doesnt work try doing alt-f2 and it should bring up a "run" box and you should be able to enter the command gnome-terminal which you installed or xterm which is the basic terminal that comes with the install. for some reason the gnome-terminal didnt automatically set it self in the menu so the easiest way is to do a locate command to find the gnome-terminal executable and from there you will be able to add an entry to the /usr/share/application folder where the menu items are located. each item in the folder is a .desktop item which adds itself to the menu automatically. so try viewing a few of them and create a new .desktop file with the gnome-terminal info and it should autogenerate a menu ntry for it. but first id look in the area i suggested earlier to find the terminal. if it only shows a $ try to "su" to your user name and you should have it. maybe leave it open all the time?  if you need more assistance find my nick "soldats" on #ubuntu or #ubuntu-us-az and ill be happy to help you   :)

Alt-F2 - xterm works  :)

 ... it's a workaround but for now I'll live with that (cuz I'm cooking supper )

---

### Post by soldats on 2008-02-29
awesome im very glad you got at least a part of your problem solved.if you need more help try asking in #xubuntu or #xfce (ask precisely for xubuntu help) on irc  or look for me on irc as well .....
:)

---

### Post by Bruce M. on 2008-03-01
> **soldats said:**
> awesome im very glad you got at least a part of your problem solved.if you need more help try asking in #xubuntu or #xfce (ask precisely for xubuntu help) on irc  or look for me on irc as well .....
:)

Thanks for the offer but I don't do IRC  :)

---

### Post by Bruce M. on 2008-03-01
Before deleting GNOME Terminal I did some research and found out how to create "Launchers" in XFCE.

Desktop is easy:

Right Click - select Create Launcher
In Name: Terminal
I see two different types of Terminals only differing by Icons:
[LIST=1]
[*][>_] - is the Gmome Terminal.
[*][$ ] - the full screen command line that I can't figure out how to exit.
[/LIST]

No more Alt-F2 - xterm for me (can't cut and paste it that either.

Panel is easy too:
Name: Terminal
Description ( I always leave this blank, but your choice)
Icon: /usr/share/pixmaps/gnome-terminal.png
Command: gnome-terminal
 - Use startup notification

Perfect!
Bruce

---

