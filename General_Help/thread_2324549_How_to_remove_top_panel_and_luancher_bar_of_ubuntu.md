---
title: "How to remove top panel and luancher bar of ubuntu desktop 16.04"
date: 2016-05-14
forum: General Help
---

### Post by gzliudan on 2016-05-14
Hello, all:
    I need to create a blank desktop for one user under ubuntu desktop 16.04, or any ubuntu 16.04 branch. This user will run a GUI program in full-screen mode at once after login, and will not never logout. The user can't switch to other program also. So I must remove or hide top panel(named menu bar or indicator) and left bar(luancher) only for this user. Does anybody know how to do it?

with best regards
daniel

---

### Post by Frogs Hair on 2016-05-14
Hello and welcome 

There is no option to remove or hide the top panel in unity. There are other desktop environments that will allow the panel to hide. These would include Kubuntu , Xubuntu, Lubuntu, and Ubuntu Mate.

Edit: Another alternative might be to install the gnome-session-flashback and select it at login. This session uses already installed applications has a panel auto-hide panel setting .```
 sudo apt-get install gnome-session-flashback
```

---

### Post by QDR06VV9 on 2016-05-14
I have moved your thread here for better chances to solution.
And please use the standard font's and size.
Thanks and Good luck

---

### Post by grahammechanical on 2016-05-14
Ubuntu uses Compiz as a window compositor and Unity is a Compiz plugin. In the past it was possible to disable the Unity plugin with the result that all we got was the desktop wallpaper. I am not sure if it is still possible to do this. But to do it install Compiz Configuration Settings Manager (CCSM) and look for something in there to disable the Unity plugin.

The application that you refer to would need to load as a startup application. And in case you ever need to shut down or restart. You would need to know how 
to open a terminal or Linux console and which commands to run. And also how to load Compiz from a terminal to re-enable the Unity plugin.

I assume you are going to test all this out first.

Regards

---

### Post by rasalhague on 2016-09-12
[http://askubuntu.com/a/823915/499381](http://askubuntu.com/a/823915/499381)

---

### Post by buzzingrobot on 2016-09-12
Panels in Xubuntu, Kubuntu and Lubuntu can be hidden or not displayed at all. If "hidden" they will display  upon cursor pressure on the display edge.

The top bar in Unity and Gnome is not intended to be a panel as in those other interfaces.

Also, with or without access to the Launcher, any Unity user can launch any program by tapping the Super key and searching for it.  What you seem to be trying to create is a "kiosk" environment, which locks users into one, and only one, program.  You can find tutorials and howto's on the web.

---

