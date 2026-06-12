---
title: "Unable to login after gnome-theme-manager crash in Edgy"
date: 2006-11-02
forum: General Help
---

### Post by Garyu on 2006-11-02
I was switching between icon sets in gnome-theme-manager when the applicaton crashed, only leaving aMSN, GAIM and Evolution running (which was on my other workspace). After doing a Ctrl-Alt-Backspace, I am no longer able to log in to my user account. ](*,) 
Bug report filed here:
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/69977](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/69977)
(my first bug report - yay) 

I did a Ctrl-Alt-F1 to access the terminal and created a new user. This user is able to log in without problems. So it seems the theme-settings are (hopefully) the only thing wrong with my user. How can I use the Ctrl-Alt-F1 terminal to restore my theme settings?

I need to know which files to alter (or delete?) in order to revert theme settings to default installation values.

---

### Post by Garyu on 2006-11-02
Alright, I fixed it... Kind of...

By renaming .gconf to .gconf.old all settings in Gnome are recreated from scratch. So all of my settings are gone, but at least I am able to log in to my user account.

So, I ran a 
```
diff .gconf .gconf.old
```
which resulted in:
Lika underkataloger: .gconf/apps och .gconf.old/apps
Lika underkataloger: .gconf/desktop och .gconf.old/desktop
Endast i .gconf.old/: GNOME
Endast i .gconf.old/: system
Endast i .gconf.old/: usr

I am including a file of the result of a "diff -r .gconf .gconf.old" if anyone would care to look at it and decide what went wrong.

---

### Post by Garyu on 2006-11-03
OK, problem solved... I know there are others out there with the same problems, cause I ran in to a couple on IRC when searching for people with some answers... So here is how you solve it:

The theme manager crashes because I selected a mouse cursor theme, which also resided in ~/.icons/ with the normal icon sets.

Just do this:
```
mv ~/.gconf/desktop/gnome/interface ~/.gconf/desktop/gnome/interface.old
```
and everything will work fine. (OR you could go there and edit the .xml file and replace the name of the mouse cursor theme with something else).

:cool:

---

