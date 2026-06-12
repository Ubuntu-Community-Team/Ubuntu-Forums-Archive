---
title: "Alacarte doesn't open"
date: 2006-10-28
forum: General Help
---

### Post by rekahsoft on 2006-10-28
I am using edgy and wanted to use alacarte...i have to be sudo to open it otherwise i get the following error/s when i run it from terminal:```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in ?
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.4/site-packages/Alacarte/MainWindow.py", line 45, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 58, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 62, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/collin/.config/menus/settings.menu'
```How do i fix this?

---

### Post by beerfan on 2006-10-28
I could be wrong (don't have Edgy) but I believe someone said that Alacarte has been replaced. Try right-clicking on the menu item to edit it?

---

### Post by rekahsoft on 2006-10-28
well, i guess i should have thaught a little more...i was frstrated...very simple fix after looking at the code and the error message...for anybody else with this probem the fix is like so:```
sudo chown -R <you_usr_name> ~/.config/menus
sudo chmod -R 777 ~/.config/menus
```

---

### Post by PriceChild on 2006-10-28
Yeah... opening alacarte with sudo will change the root accounts menus... not yours ;)

I reccomend a good
```
sudo chown <<username>>:<<username>> -R /home/<<username>>
```once in a while to make sure you can do everything in your home dir.

---

### Post by the_french_canadian on 2006-10-28
Alacarte no longer appears in the Applications menu, but i can still access it through by inputting *alacarte* into *run application* (open *run application* by pressing [ALT] + [F2])

---

### Post by PriceChild on 2006-10-28
System>Preferences>Menu Layout

Will open it up for you.

---

### Post by beerfan on 2006-10-28
> **PriceChild said:**
> System>Preferences>Menu Layout

Will open it up for you.

Hrm, would have been nice if you could just right-click the menu item to modify it like in most other apps. Oh well...maybe in Gnome 3.0 :-)

---

### Post by rekahsoft on 2006-10-28
> **PriceChild said:**
> Yeah... opening alacarte with sudo will change the root accounts menus... not yours ;)

I reccomend a good
```
sudo chown <<username>>:<<username>> -R /home/<<username>>
```once in a while to make sure you can do everything in your home dir.

yes this is the thing to do becuase you run into more issues down the road :)

---

