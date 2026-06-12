---
title: "Using workspaces"
date: 2007-05-25
forum: General Help
---

### Post by mad scientist on 2007-05-25
I am as new as they come with Ubuntu, so please correct me where I am wrong (it is the only way I will learn).  

After I installed Ubuntu 7.04 I decided to install avant window navigator.  When I did this I deleted the default panel on the bottom of the desktop which contained the workspace navigation.  This leaves me with my top panel.  I know you can add the "Switch Between Workspaces" button to this panel, but when I do this it only shows me my current workspace.  

What am I doing that I cannot see my other workspaces. 
In fact, I am not even quite sure how to move applications to other workspaces.  This may become more clear once I actually can manipulate those spaces.

I am sorry if this has been discussed but maybe I did not use the right search terms when I was looking for help already posted.

Thanks in advance! :)

---

### Post by ayoli on 2007-05-25
what do you use as window manager/decorator
if metacity:
you can switch workspace with CTRL + ALT + left|right arrows
you can move apps on other workspaces by right clikin on the title bar and pick "move to workspace .." option
if beryl/compiz:
same to switch workspaces, and also this possibility: CTRL + ALT + PageDown
to move windows on other workspace CTRL + ALT + SHIFT + left|right arrow

---

### Post by mad scientist on 2007-05-25
> **ayoli said:**
> what do you use as window manager/decorator
if metacity:
you can switch workspace with CTRL + ALT + left|right arrows
you can move apps on other workspaces by right clikin on the title bar and pick "move to workspace .." option
if beryl/compiz:
same to switch workspaces, and also this possibility: CTRL + ALT + PageDown
to move windows on other workspace CTRL + ALT + SHIFT + left|right arrow

I use Beryl for my manager/decorator.  I tried to both move windows to other work spaces and to switch workspaces but both did not work.  I am beginning to think I do not have other workspaces :(

---

### Post by ayoli on 2007-05-25
see the settings i have in beryl configurator (attached screenshot)
you should have 4 for virtual horizontal size.

---

### Post by mad scientist on 2007-05-25
> **ayoli said:**
> see the settings i have in beryl configurator (attached screenshot)
you should have 4 for virtual horizontal size.

I have that already.  I also checked my keyboard shortcuts and to move to workspace left right it is shift+ctrl+alt+left/right arrow, but still nothing happens.

Btw, thanks for taking the time to help.

---

### Post by ayoli on 2007-05-25
what does happen when you hold CTRL and ALT key + left mouse click and moving your mouse ? is the cube moving ?

edit: you may want to try [screenlets]("http://ubuntuforums.org/showthread.php?t=444158&highlight=screenlets") which have a pager (desktop switcher).

---

### Post by mad scientist on 2007-05-25
> **ayoli said:**
> what does happen when you hold CTRL and ALT key + left mouse click and moving your mouse ? is the cube moving ?

Nothing happens, I do not even see a cube.

---

### Post by ayoli on 2007-05-25
in a terminal type in:
```
ps aux |grep beryl
```
post output here

---

### Post by mad scientist on 2007-05-25
Here is what I get:
```
root     27392  0.0  0.0   2880   764 pts/0    S+   16:26   0:00 grep beryl

```

---

### Post by ayoli on 2007-05-25
means beryl isnt running
do you have beryl icon in the systray ? if so check beryl as window manager (as you can see on the attached screenshot)
if you don't have beryl icon in your systray, hit ALT + F2 and type in:
```
beryl-manager
```
if you have not already done that put it in your startup progs:
menu System > Preferences > Sessions then pick startup progs tab, claick add button and add beryl-manager.

---

### Post by mad scientist on 2007-05-25
> **ayoli said:**
> means beryl isnt running
do you have beryl icon in the systray ? if so check beryl as window manager (as you can see on the attached screenshot)
if you don't have beryl icon in your systray, hit ALT + F2 and type in:
```
beryl-manager
```
if you have not already done that put it in your startup progs:
menu System > Preferences > Sessions then pick startup progs tab, claick add button and add beryl-manager.

Merci Ayoli. This worked perfectly.  I have workspaces again!

---

