---
title: "Creating a script"
date: 2006-11-25
forum: General Help
---

### Post by umanzor on 2006-11-25
Hi!

In order to run beryl, I need to run it with these two commands

```
emerald &
```
```
beryl &
```

Otherwise it won't work. How do I make a script, so this commands run automatically. Is it possible to make them run BEFORE everything else?

---

### Post by po0f on 2006-11-25
umanzor,

Why don't you use `beryl-manager` instead?  Boot into a normal GNOME session, hit Alt+F2, type in "beryl-manager", and click OK.  Right-click on beryl's tray icon, go to "Select window manager", and click on Beryl.

[EDIT]

If you find that everything works, you can start it up every login by navigating to System->Preferences->Sessions, click on the Startup Programs (or something like this) tab, and click on add a new entry.  Type in "beryl-manager".  Log out and log back in to test to see if it works.

---

### Post by umanzor on 2006-11-27
It's pretty much random, sometimes it works, other times it will load without borders.

But the emerald & and beryl & commands work everytime

---

### Post by Ramses de Norre on 2006-11-27
Paste this in a file:
```
#!/bin/bash
emerald &
beryl &
```
then make it executable and add the full path to it to the startup programs.

---

