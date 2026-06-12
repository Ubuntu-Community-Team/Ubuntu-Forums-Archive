---
title: "Main Menu (Alacarte) Not Working"
date: 2012-11-22
forum: General Help
---

### Post by stevedude on 2012-11-22
I'm running Ubuntu 12.10 64-bit and up until a couple of weeks ago, I was able to run "Main Menu" (the "Alacarte" program) with no issues. I did install some additional programs since then, but can't recall what they are.

When launching Alacarte from terminal, I receive this message:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 43, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 31, in __init__
    self.load()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 45, in load
    raise ValueError("can not load menu tree %r" % (self.name,))
ValueError: can not load menu tree 'applications.menu'


I have reinstalled alacarte and gnome-panel via Synaptic Mananger, but nothing is working. I would appreciate any assistance with this. Thanks!

---

### Post by stevedude on 2012-11-28
Had to edit the alacarte.desktop file to run as root. That was the only way to get alacarte to function as a work-around. 

For anyone interested I edited the Exec line as follows: Exec=gksudo -k -u root alacarte

---

### Post by Heinrich_Evers on 2013-02-06
> **stevedude said:**
> Had to edit the alacarte.desktop file to run as root. That was the only way to get alacarte to function as a work-around. 

For anyone interested I edited the Exec line as follows: Exec=gksudo -k -u root alacarte

Yes, but how do you get it back so that normal users can use it and it's function displays to the Gnome menu?

---

