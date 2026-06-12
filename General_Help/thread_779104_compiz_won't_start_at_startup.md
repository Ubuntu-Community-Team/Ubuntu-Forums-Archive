---
title: "compiz won't start at startup"
date: 2008-05-02
forum: General Help
---

### Post by Zaff on 2008-05-02
Hi all, I have two, maybe related problems. I just upgraded to Hardy a few days ago and installed the Nvidia latest beta driver to get my Geforce 7600 GS to work properly. Now I had compiz before and it worked well, if not for the fact that if I put startup program in the System -> Preferences -> Session menu, it would not save them when I turned my computer off. Not really needing it, I never really thought about it.
My problem is now this : Compiz won't load at start up anymore. Which means the decorator won't load and I have to start fusion-icon from a terminal to get everything to work. This doesn't happen if I use metacity... I tried adding fusion-icon to the startup thing in Session but same as before, it just won't keep it in there.
Another issue I think could be related is that when I shut down or log out, it'll unload pretty much everything and leave me with just my desktop background and my mouse on the screen and stay there. It's not frozen (the mouse works) and I can kill it with Ctrl - Alt - Backspace.
I don't know if this second problem is related or not but if someone could point me in the right direction, I've gotten used to compiz and I like it !
Thanks

Edit : So I just tried using the gnome-session-properties app from the terminal to see if there would be any error message and there were :
> 
** (gnome-session-properties:4977): WARNING **: Could not save /home/zaf/.config/autostart/fusion-icon.desktop file

I tried changing the permissions on that directory (owned by root by the way) but it didn't change anything. It only contains two files : beagled.desktop and beryl-manager.desktop. I tried to move that file outside, wondering if there was a sort of weird incompatibility but it didn't change anything either...

---

### Post by Zaff on 2008-05-03
so I created a fusion-icon.desktop file in the directory and now it works. I still don't understand why the GUI couldn't create the file...
Has anyone encountered this issue before ?

---

### Post by nge on 2008-05-03
I had this issue after installing 0.7.2.

Fixed it by entering this line manually in session manager (startup programs)

```
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering
```

I got that line by doing fusion-icon manually in terminal. Scroll up .. It's located a few lines after the start. Note: make sure that the settings are all set, then double check by quitting fusion-icon and running it again.

---

