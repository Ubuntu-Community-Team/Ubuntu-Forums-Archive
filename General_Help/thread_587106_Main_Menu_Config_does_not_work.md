---
title: "Main Menu Config does not work"
date: 2007-10-22
forum: General Help
---

### Post by rudeboyskunk on 2007-10-22
Every time I click on System>Preferences>Main Menu, it begins to load, but then nothing happens.  I don't know the command line command, so I cannot give a terminal readout.  Anybody else have this problem?  Any way to solve it?  Does it have to do with Compiz?

---

### Post by nikef on 2007-10-22
just checked mine and loads up ok

---

### Post by rudeboyskunk on 2007-10-23
Anybody still have an idea about this?

What's the terminal command to bring up the Main Menu config editor?  This is for System>Preferences>Main Menu in Gutsy.

---

### Post by Chunk of Earth on 2007-10-23
In feisty it's alacarte. Haven't tried gutsy yet.

---

### Post by por100pre1 on 2007-10-23
> **Chunk of Earth said:**
> In feisty it's alacarte. Haven't tried gutsy yet.

It is Alacarte in Gutsy too.

```
alacarte
```

---

### Post by rudeboyskunk on 2007-10-23
Ok, I'll try as soon as I get home and post results.  Thanks!

---

### Post by rudeboyskunk on 2007-10-24
Ok, I tried it, and I have to do "sudo alacarte" to get it to work.  When I just type "alacarte," this is what I get:

> /usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/rudeboyskunk/.config/menus/applications.menu'


Why won't it just ask me for root password when I click on the icon?

---

