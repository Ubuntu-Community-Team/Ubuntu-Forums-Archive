---
title: "How do I embed the i8kmon applet in the Gnome Panel?"
date: 2006-07-03
forum: General Help
---

### Post by vayu on 2006-07-03
I've installed the i8kutils from synaptic, but that didn't put an option in the menu to add the applet to panel like I read.  Supposedly this applet will embed in the Gnome panel.  I made an application launcher for it with command "i8kmon &".  That creates an icon on the panel which runs the applet in a window on the desktop but doesn't run the actual applet in the panel.

---

### Post by mlwalla on 2007-03-01
I don't know if you ever got an answer to your question, but I am wondering the same thing.

---

### Post by mlwalla on 2007-03-12
And, after an email to the developer of i8kmon, I have an answer!  There is a package called gnome-swallow-applet that will let you swallow the window into the panel.  Just 
```
sudo apt-get install gnome-swallower-applet
```
Then, right click the panel, choose 'add to panel' and choose 'Swallower Meta-Applet', which pops up a window asking you what program to run and what the name of the window is that you want to 'swallow' into the panel.  I use i8kmon -a (to turn the fans on and off according to a preset temperature range), but the window is just named 'i8kmon'.

Now my keyboard is no longer frighteningly warm to the touch, AND the gauge sits nicely in the top panel so that I can keep an eye on it!

---

### Post by martyvona on 2007-05-07
I think slight typo above, or maybe the name changed, I needed to do

```
sudo apt-get install gnome-swallow-applet
```

NOT

```
sudo apt-get install gnome-swallower-applet
```

---

