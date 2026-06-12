---
title: "Lost my compiz Icon, Help please."
date: 2006-08-21
forum: General Help
---

### Post by simoncoul on 2006-08-21
Hi,

I accidently removed the compiz icon at the top of my screen when I was trying to remove something else.  I was woundering if someone could tell me how to get it back please.

Thanks

---

### Post by BitTorrentBuddha on 2006-08-21
What did the icon do? If it was for toggling compiz on and off, replace it with this script, if you need further help as to how to do this, just ask. ```
#!/bin/bash
if ps -A | grep -e " compiz.real$" > /dev/null; then
	killall cgwd
	metacity --replace &
else
	cgwd &
	compiz --replace gconf &
fi
```

---

### Post by simoncoul on 2006-08-21
Yeah I don't really know what to do with that sorry.  But I already have a script called compiz-start.py, and compiz still runs and so does CGWD but,  But the icon to do the toggling is now missing.   So a bit more information would be helpful.

```

#! /usr/bin/python

import os
import pygtk
pygtk.require('2.0')

import gtk, gobject
import egg.trayicon

def start_compizdefault():
	try:
		os.system("killall gnome-window-decorator 2> /dev/null")
		gobject.spawn_async(['cgwd', '--replace'], \
				     flags=gobject.SPAWN_SEARCH_PATH)
		gobject.spawn_async(['compiz', '--replace', 'gconf'], \
				  flags=gobject.SPAWN_SEARCH_PATH)
	except gobject.GError:
		os.system("killall cgwd 2> /dev/null")
		gobject.spawn_async(['gnome-window-decorator', '--replace'], \
				     flags=gobject.SPAWN_SEARCH_PATH)
		gobject.spawn_async(['compiz', '--replace', 'gconf'], \
				  flags=gobject.SPAWN_SEARCH_PATH)
	

def start_compiz():
	os.system("killall cgwd 2> /dev/null")
	gobject.spawn_async(['gnome-window-decorator'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)

def start_compizcgwd():
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['cgwd', '--replace'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)

def start_metacity() :
	os.system("killall gnome-window-decorator || killall cgwd 2> /dev/null")
	gobject.spawn_async(['metacity', '--replace', 'gconf'], \
			     flags=gobject.SPAWN_SEARCH_PATH)

def logoutsession() :
	os.system("gnome-session-save --kill --gui")

def place_menu(menu):
	(width, height) = menu.size_request()
	(menu_xpos, menu_ypos) = tray.window.get_origin()
	menu_xpos = menu_xpos + tray.allocation.x
        menu_ypos = menu_ypos + tray.allocation.y
	if menu_ypos > tray.get_screen().get_height() / 2:
                menu_ypos -= height + 1
        else:
                menu_ypos += tray.allocation.height + 1

        x = menu_xpos;
        y = menu_ypos;
        push_in = True;
	return (x, y, push_in)

def configure_menu_activate(widget):
	gobject.spawn_async(['gconf-editor'], flags=gobject.SPAWN_SEARCH_PATH)
#	will be reimplemented once gset-compiz is updated.
#	try:
#		gobject.spawn_async(['gset-compiz'], flags=gobject.SPAWN_SEARCH_PATH)
#         
#	except gobject.GError:
#		gobject.spawn_async(['gconf-editor'], flags=gobject.SPAWN_SEARCH_PATH)

def compiz_menu_activate(widget):
	start_compiz()

def metacity_menu_activate(widget):
	start_metacity()

def cgwd_menu_activate(widget):
	start_compizcgwd()

def logoutsession_activate(widget) :
	start_metacity(), logoutsession()

def quit_menu_activate(widget):
	gtk.main_quit()

def callback(widget, ev):
	menu.set_screen(widget.get_screen())
	menu.popup(None, None, place_menu, ev.button, ev.time)

def gcompizthemer_menu_activate(widget):
	gobject.spawn_async(['gcompizthemer'], flags=gobject.SPAWN_SEARCH_PATH)

def dock_activate(widget):
	gobject.spawn_async(['dock'], flags=gobject.SPAWN_SEARCH_PATH)

def dock_deactivate(widget):
	os.system("killall dock")

menu = gtk.Menu()
item = gtk.ImageMenuItem(stock_id=gtk.STOCK_PREFERENCES)
item.connect("activate", configure_menu_activate)
menu.append(item)
item = gtk.ImageMenuItem( "Theme Selector" )
item.connect("activate", gcompizthemer_menu_activate)
_img = gtk.Image()
_img.set_from_stock("gtk-select-color", gtk.ICON_SIZE_BUTTON)
item.set_image(_img)
menu.append(item)
item = gtk.SeparatorMenuItem()
menu.append(item)
item = gtk.MenuItem("Gnome Window Decorator")
item.connect("activate", compiz_menu_activate)
menu.append(item)
item = gtk.MenuItem("Metacity")
item.connect("activate", metacity_menu_activate)
menu.append(item)
item = gtk.MenuItem("Compiz Window Decorator")
item.connect("activate", cgwd_menu_activate)
menu.append(item)
item = gtk.SeparatorMenuItem()
menu.append(item)
item = gtk.MenuItem("Kiba-Dock")
item.connect("activate", dock_activate)
menu.append(item)
item = gtk.MenuItem("Kill Kiba-Dock")
item.connect("activate", dock_deactivate)
menu.append(item)
item = gtk.SeparatorMenuItem()
menu.append(item)
item = gtk.MenuItem("Log Out")
item.connect("activate", logoutsession_activate)
menu.append(item)
item = gtk.SeparatorMenuItem()
item = gtk.ImageMenuItem(stock_id=gtk.STOCK_QUIT)
item.connect("activate", quit_menu_activate)
menu.append(item)
menu.show_all()

tray = egg.trayicon.TrayIcon("TrayIcon")
box = gtk.EventBox()
pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/compiz/logo24.png")
image = gtk.Image()
image.set_from_pixbuf(pixbuf)
box.add(image)
tray.add(box)
tray.show_all()
	
box.connect("button-press-event", callback)

start_compizdefault()

gtk.main()

```

That is the script I'm using it had more then just toggling tho, which was very very very useful when like CGWD messed up I could just kill it but compiz effects would still work with GWD.

---

### Post by BitTorrentBuddha on 2006-08-21
Oh, you had that fancy notification area compiz toggler, I'm envious, but I don't know how to set that up, sorry.

---

