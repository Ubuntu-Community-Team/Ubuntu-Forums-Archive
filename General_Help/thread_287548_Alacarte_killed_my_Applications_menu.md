---
title: "Alacarte killed my Applications menu"
date: 2006-10-28
forum: General Help
---

### Post by keithkiss on 2006-10-28
Alacarte killed my Applications menu.

I went into Alacarte and tried to add something.
Since then my Applications doesnt work or everything was deleted.

I went into the terminal and type "alacarte" and this is what I get:



---------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
    self.loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 201, in loadMenus
    self.app_handler = MenuHandler('applications.menu', self.options)
  File "/usr/lib/python2.4/site-packages/Alacarte/PyXDGMenuHandler.py", line 27, in __init__
    xdg.MenuEditor.MenuEditor.__init__(
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 40, in parse
    self.menu = parse(menu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 508, in parse
    raise ParsingError('Not a valid .menu file', filename)
xdg.Exceptions.ParsingError: ParsingError in file '/home/k/.config/menus/applications.menu', Not a valid .menu file


---------------------------------------------------------------------




Any idea how I can fix this?
Im using Ubuntu 6.06

Thanks so much,
Keith

---

### Post by ayllu on 2006-11-09
did you solved, i have the same problem

---

### Post by ayllu on 2006-11-09
I know... the problem... is yor file /etc/xgd/applications.menu and the other are prefernces.menu and settings.menu, your file is corrupt, and you need to replaceit, I tried whit some code but it's not the original buts works, but i can not fix the system menu.

---

