---
title: "Have lost titlebar on all windows"
date: 2007-05-22
forum: General Help
---

### Post by eroica on 2007-05-22
hello,
I'm new to ubuntu & gnome and was trying to personalize my login screen and downloaded a login theme from art.gnome dragged it into gdkmanager per instructions and logged off and back on. now I have no titlebar on any window (min,max,close etc..). I googled the trouble and issued the command "rm -rf .gnome .gnome2 .gconf .gconfd .metacity" and that did reset my desktop but unfortunately still have no titlebars. when i even try to select window manager from preferences i get an error message saying something about no file being found for theme??? I really dont want to have to do a reinstall any suggestions on how to correct this would be appreciated.
thanx.....

---

### Post by the_it on 2007-05-22
I'm guessing that your metacity / gtk-window-manager (i don't know the name) isn't being automatically started on session start?  Try manually starting metacity from the command-line and see if titlebars come back.

---

### Post by eroica on 2007-05-22
Yep that did it!  But I have to keep the terminal window open. If I close it I revert back to no titlebar. Also  starting metacity this way is consuming 100% CPU.how do i have it start automatically in the backround? I'm hoping then it wont consume so many resources....
thanx

---

### Post by strabes on 2007-05-22
You can put an "&" behind it if you start it from terminal to run it in the background.

---

### Post by eroica on 2007-05-22
ok but still how do i correct this situation so my window manager starts on bootup?

---

### Post by the_it on 2007-05-22
this isn't the best way to do it, but you can start metacity manually by using your gnome-session-properties to load metacity on startup.

go to system->preferences->sessions
or
alt+f2 gnome-session-properties

Then in Startup Programs, add a new program called Metacity
Name: Metacity
command: metacity

metacity should then autostart.

But this isnt the normal way metacity is started.  you see, metacity should be part of the normal gnome startup (before the session loading thing), and it turns out that your theme probably replaced the normal startup with something else.  It probably won't make any difference whatsoever, but it irks me when I "break" my system like that and make a nonstandard hack to fix it.

1) Could you post a copy of the script used to install the theme, or maybe a link to the theme itself?  Hopefully we can reverse the damage it did if we know what it did.
2) Could you try creating a new guest account, logging in to that guy, then seeing if metacity loads alright for him (does he have titlebars even without you altering the gnome-session-properties?)

---

### Post by eroica on 2007-05-23
the login theme was a .tar.gz that I just dropped into gdkmanager. here is the link to it:
[http://art.gnome.org/themes/gdm_greeter/1350](http://art.gnome.org/themes/gdm_greeter/1350)

I did create a guest account and metacity loaded fine. What I did to solve problem in my main account was start metacity& at a terminal and then went into session and clicked the session options tab and clicked save current option. Now metacity loads on startup. But like u say I dont see verification that windows manager is loading on the initial gnome splash screen. Last thing I see loading is nautilus. I, like u, dont like using hacks so if u have any suggestions i'd like to hear them....

---

### Post by the_it on 2007-05-24
Oh my hasty reading.  I thought it was a gnome theme you downloaded and not a gdm theme.

Question: Does changing your theme back to human or gnome theme make your titlebars go back in gnome?

Also, I was comparing the desktop/gdm theme to the other desktop themes on my box (I don't want to install it myself ;p) and I noticed it had a funky line.

Themes are placed in /usr/share/gdm/themes, under individual folders.  To my knowledge, gdm just scans each folder for a .desktop file which points to the xml file that contains settings.  Here's the Human file:

```
[GdmGreeterTheme]
Greeter=Human.xml
Name=Human
Description=Ubuntu Default Welcome Theme
Description[fr]=Thème de bienvenue par défaut d'Ubuntu
Author=Jeff Waugh, Mark Shuttleworth, Jozef Mak, Jonathan Austin, Frank Schoep
Copyright=(c) 2004-2006 Canonical Ltd.
Screenshot=screenshot.png

```

Here's the one in the theme you downloaded

```
[GdmGreeterTheme]
Greeter=Prof3ta.xml
Name=Prof3ta
Description=Prof3ta GDM Theme
http://prof3ta.netsons.org
Author=Prof3ta
Copyright=Free Art Licence
Screenshot=screenshot.png
```

notice the [http://prof3ta](http://prof3ta) link on a separate line from something.  Appears to be a syntax error.  I suppose gdm has troulbe reading the theme because of that.  Try deleting that line, then removing metacity from your startup and see if it autostarts.

Also, try noting any other programs missing in your startup (if there are any) and see if they come back too.

---

### Post by eroica on 2007-05-26
no, reverting back to human theme was first thing I did and it had no effect. Also I heve already deleted that gdm theme from my box....

---

### Post by yapel on 2007-06-03
I have similar missing titlebar problem.

What I did just before this happened was to change the screen type to LCD, and screen size from 1024x768 to 1440x900 due to change of monitor.

One other problem together with this was the login screen is now showing only a portion of the full screen, and I need to push the cursor towards the edges to see the remaining portions, such as the "Options" at the bottom-left of the Human login screen.

Would any one know how to bring back the full-size login screen?

p.s. The Metacity fix mentioned above did not work for me. I am still having missing titlebars with or without Metacity included in the system/preference/session.

---

