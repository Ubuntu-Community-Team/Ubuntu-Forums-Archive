---
title: "navigate to terminal launch?"
date: 2014-10-27
forum: General Help
---

### Post by seth14 on 2014-10-27
My ubuntu 14.04 system seems to have had some kind of crash that is causing it to boot to a desktop where I am only able to click with the mouse, the launcher has disappeared, and ctl+alt+t doesn't launch a terminal.  I can get into the filesystem because there is a folder on the desktop that I can open.  ctl+alt+del works, but the top of the window that includes the file/edit/whatever menus is gone on anything i can access.  The easiest way I can think of to fix this is if there is a way to navigate via a folder to a terminal launch so I can run a system upgrade.  Is there a directory where I can double click a file that will launch a terminal on ubuntu?  I can't boot into safe mode because there seems to be some issue with the screen where you can normally select it.

I booted a 14.10 flash drive to see if that allows an upgrade, but it only listed the option to delete the current operating system and reinstall, or install alongside, not upgrade.  I would rather not lose any of my data.

Many thanks for the help. If you post a Bitcoin address with your working solution I'll send a tip

---

### Post by yancek on 2014-10-27
Did you make any changes just prior to this happening or were you trying to make some system change?

> ctl+alt+t doesn't launch a terminal

Make sure Caps Lock is off.  If you can open a folder/directory on your Desktop in the file manager, you can navigate to /usr/bin/ directory and right-click on gnome-terminal and the first option in the menu should be Run, just click that to open a terminal.  If you can't do that, a little more detail about exactly what you can do.

---

### Post by grahammechanical on 2014-10-27
What does Ctrl+Alt+F2 do? If that gets you to a Linux command line you can run

```
sudo apt-get update
sudo apt-get upgrade
```

But I think that you need to do more than that. This will reset Compiz the window compositor

```
dconf reset -f /org/compiz/
```

This will restart Unity

```
setsid unity
```

To get back to the desktop press Ctrl+Alt+F7

Regards.

---

### Post by seth14 on 2014-10-27
Ctl-alt-f2 works.  I ran the upgrade and it finished, but it still says I'm running 14.04.1.  Compiz reset returns: error: cannot autolaunch d-bus without x11 $display.  Setsid unity returns: execvp: no such file or directory

Edit: fixed with help from these threads:
http://ubuntuforums.org/showthread.php?t=2238678

http://www.techsupportforum.com/forums/f64/setsid-unity-command-errors-876177.html#/forumsite/20517/topics/876177

---

