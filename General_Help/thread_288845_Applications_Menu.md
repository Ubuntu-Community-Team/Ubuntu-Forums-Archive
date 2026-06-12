---
title: "Applications Menu"
date: 2006-10-30
forum: General Help
---

### Post by RuarriS on 2006-10-30
Whenever I click on the "applications" button on my gnome panel, nothing happens. However menus appear when i click on "places" or "system", just nothing for "applications". I tried re-installing gnome panels, restarted x, rebooted, nothing. 

Also as a side note, when I load WoW through wine, it just seems to freeze everything. Music will still play if i'm listening, and the mouse moves, but i cannot restart the x server or do anything.

---

### Post by CatKiller on 2006-10-30
It sounds to me like you may have an entry in your Applications menu that your computer doesn't like. You could see if pressing **Alt**-**F2** and then typing **alacarte** will let you fix or remove whatever you've added recently that's messed it up.

---

### Post by RuarriS on 2006-10-30
o thanks, it was actually spitting out the error that i had created a menu without a name, so i opened the config file "~/.config/menus.applications.menu" and deleted the appropriate lines

---

### Post by CatKiller on 2006-10-30
Excellent. Glad you got it fixed.

---

### Post by volanin on 2006-10-30
I also have an annoying problem with the Applications Menu:

Whenever I create or delete a new entry in Alacarte, it does NOT update.
I have to do 'killall gnome-panel' everytime too see the changes.

Strangely, it does not happen when I click Clear Recent Documents.
The list is updated (cleared) instantly.

---

### Post by happy-and-lost on 2006-10-30
WoW issue... what's your glxinfo output?

---

### Post by RuarriS on 2006-10-31
> **happy-and-lost said:**
> WoW issue... what's your glxinfo output?

typing glxinfo into a prompt returns what i've copied into the attached file

---

### Post by ayllu on 2006-11-09
The problem is that yor file etc/xgd/applications.menu is empty and corrupt, well try to replace it. Don't ask me how... ipm tring to do it, but i got the problem beause y tried to execute alacarte from the kernel and i get that this file is corrupt. if you can do it, post the file.
-----------------------
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
xdg.Exceptions.ParsingError: ParsingError in file '/home/k/.config/menus/applications.menu',

---

### Post by CatKiller on 2006-11-09
What happens if you just delete the broken file? Do you get a shiny new one created for you?

EDIT: Actually, don't do that. I haven't tried it, but I'd misread the file that you said was the problem. The file ~/.config/menus/applications.menu **should** be OK to delete. Other files, not so much.

---

### Post by jms830 on 2006-11-09
cat killer: back it up and find out! :)

---

### Post by CatKiller on 2006-11-09
> **jms830 said:**
> cat killer: back it up and find out! :)

I *like* **my** menu :roll: :D

---

