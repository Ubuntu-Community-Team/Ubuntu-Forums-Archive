---
title: "How to get rid of blue border on all active windows?"
date: 2019-09-01
forum: General Help
---

### Post by mijaillinares on 2019-09-01
Hi everyone,

I've just done a fresh installation of Lubuntu and loving it's speed. However, I've gotten a bit frustrated trying to get rid of a blue border that appears on all active windows.

Would anyone happen to know how to disable this, change colors, add transparency?

Thank you so much!

Mijail

---

### Post by HermanAB on 2019-09-01
do you do?

---

### Post by ajgreeny on 2019-09-01
@ mijaillinares

Welcome to the forum.
Please note that I have reinstated the text of your post.
If the problem is now solved please tell us how; also please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by dragonfly41 on 2019-09-01
Posts have got out of sync.
I don't have Lubuntu but I would look at System Settings. Top right icon on toolbar next to time display.

---

### Post by again? on 2019-09-01
See below...

---

### Post by again? on 2019-09-01
Look in openbox settings.
This is the window manager that controls decorations. (border and titlebar)
Can't find try in terminal...
```
obconf-qt 
```
or
```
obconf
```

Choose a different theme.

---

### Post by guiverc on 2019-09-01
I don't understand what 'blue' you mean, but it could be because my settings have been altered from defaults.

To get into Openbox Configuration use Menu -> Preferences -> OpenBox Configuration Manager

or follow the manual - [https://manual.lubuntu.me/3/3.2/3.2.11/openbox_settings.html](https://manual.lubuntu.me/3/3.2/3.2.11/openbox_settings.html) which will explain it far better than I could.

You didn't tells us your release (of Lubuntu); so I've assumed Lubuntu 19.04.

---

### Post by Dennis N on 2019-09-01
The (default?) Lubuntu Arc theme has the blue border around the window in focus (unfocused, the border is black).
As suggested by others, it's a simple matter to change the Openbox theme. I find the path to the Openbox settings dialog in Lubuntu 19.04 as:
[B]Menu > Preferences > LXQt Settings > Openbox Settings
[/B]
You can probably edit the border color and other theme colors in the themerc file located at:
/usr/share/themes/LubuntuArc/openbox-3/themerc

Transparency is possible!
Activation:
Menu > Accessories > Compton
Activate this on startup:
Menu > Preferences > LXQt Settings > Session Settings < checkbox

You can customize window shadows and transparency from:
Menu > Preferences > LXQt Settings > Window Effects

After changes, you log out and log In to new session.

---

### Post by snugglej2 on 2019-10-12
Hey

I see that also on the 19.04 install of lubuntu. It looks to be part of the Lubuntu Arc theme. You can just go to Window Manager Preferences and then just change the theme to Arc-Darker or something else and the blue border goes away.

See focused window as an example around the whole window there is a border of blue.
[IMG]https://i.imgur.com/Ma2qS4x.jpg[/IMG]

---

