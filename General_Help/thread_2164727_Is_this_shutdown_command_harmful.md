---
title: "Is this shutdown command harmful?"
date: 2013-08-01
forum: General Help
---

### Post by Colorblind_Clown on 2013-08-01
Hello,

My Ubuntu build is 12.04 Mini with blackbox and a few other installed programs. I do not want to use sudo to have to shutdown the computer. I found a command on a few websites that I have been using but I'm not sure if it is safe to use. The command is below.

```
Shutdown
dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

Restart
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot

Suspend
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

Hibernate
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate
```

Any information would be helpful.

Thanks

---

### Post by GwL3eNC on 2013-08-01
Hi, 

sorry the commands i dont know. But take a look at 

sudo visudo

There you can define user which is allowed to use shutdown without sudo.
Seems adding these lines

# User alias specification
User_Alias ABSCHALTER = otto, anna, berta

# Cmnd alias specification
Cmnd_Alias DOWN = /sbin/shutdown, /sbin/halt, /sbin/reboot

# User privilege specification
ABSCHALTER ALL = NOPASSWD: DOWN

at the end of the file helps. Found it on a german site
[http://wiki.ubuntuusers.de/Herunterfahren](http://wiki.ubuntuusers.de/Herunterfahren) 
Also you can allow every user the shutdown with
sudo chmod +s /sbin/shutdown 
Hope it helps

---

### Post by Colorblind_Clown on 2013-08-01
Thanks for the quick response [**[COLOR=#000000]GwL3eNC[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841512"). I have tried editing the visudo file before and unfortunately, every time I did I managed to break the sudo command and had to use a livecd to undo the changes. My main concern with the commands that I originally posted is that I do not want to accidentally corrupt something on the computer by using them.

---

### Post by GwL3eNC on 2013-08-01
With some little differences your commands found also on my posted link. Normally you can trust
this, so i dont think that the commands are bad. But please wait a bit for another guy telling
you the same.

---

### Post by dcstar on 2013-08-02
Those commands are used by the Desktop to control the system, they are as safe as using the menus to shut the system down.

---

### Post by Colorblind_Clown on 2013-08-02
Thanks for the responses. Based on what I am reading, it appears that the commands are safe. Also, I have written a few programs using them for anyone using openbox/blackbox that needs a shutdown menu.

Bash Script In Terminal:
```
#!/bin/bash
clear
echo -n """+-------------+
| 1. Restart  |
| 2. Shutdown |
|             |
| 3. Cancel   |
+-------------+

Choice (Default 3): """
read option
if [ "$option" == "1" ]; then
    dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
elif [ "$option" == "2" ]; then
    dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
else #Cancel or bad key
    echo "Program Cancelled"
fi
```

Bash Script Using xmessage:
```
#!/bin/bash

#xmessage idea from http://linux.byexamples.com/archives/87/using-gui-dialog-box/


option=$(xmessage -center "Are you sure you want to shut down your computer?" -buttons Restart,Shutdown,Cancel -print)

if [ "$option" == "Cancel" ]; then
    echo "Exit"
elif [ "$option" == "Restart" ]; then
    dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Ha/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
elif [ "$option" == "Shutdown" ]; then
    dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
fi
```

Using Python:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#

import os
def main():
    os.system("clear")
    print """+-------------+
| 1. Restart  |
| 2. Shutdown |
|             |
| 3. Cancel   |
+-------------+
"""
    option = raw_input("Choice (Default 3): ")
    if option == "1":
        os.system("dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot")
    elif option == "2":
        os.system("dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown")
    else: #Cancel or bad key
        print "Program Cancelled"
    return 0

if __name__ == '__main__':
    main()
```

Using Python with gtk:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import pygtk
pygtk.require('2.0')
import gtk
import os
class pypower:
    def killswitch(self,widget,event):
        if event == "restart":
            os.system("dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot")
        elif event == "shutdown":
            os.system("dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown")

    def __init__(self):
        screen = gtk.gdk.Screen()
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Power Options")
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_border_width(5)
        self.window.connect('delete-event', lambda window, event: gtk.main_quit())
        
        Voverframe = gtk.VBox(False)
        Hoverframe = gtk.HBox(False)
        
        
        vbox = gtk.VBox(False, 5)
        vbox.set_border_width(5)

        btnrestart = gtk.Button()
        restartbox = gtk.HBox(False, 12)
        btnrestart.add(restartbox)
        iconlogout = gtk.Image()
        iconlogout.set_from_icon_name("gnome-session-reboot",gtk.ICON_SIZE_DND)
        restartbox.pack_start(iconlogout, False,False)
        restartbox.pack_start(gtk.Label("Restart"),False,False)
        btnrestart.connect("clicked",self.killswitch,"restart")
        btnrestart.set_size_request(200,48)
        vbox.pack_start(btnrestart)

        btnshutdown = gtk.Button()
        shutdownbox = gtk.HBox(False, 12)
        btnshutdown.add(shutdownbox)
        iconlogout = gtk.Image()
        iconlogout.set_from_icon_name("gnome-session-halt",gtk.ICON_SIZE_DND)
        shutdownbox.pack_start(iconlogout, False,False)
        shutdownbox.pack_start(gtk.Label("Shutdown"),False,False)
        btnshutdown.connect("clicked",self.killswitch,"shutdown")
        btnshutdown.set_size_request(200,48)
        vbox.pack_start(btnshutdown)

        vbox.pack_start(gtk.HSeparator())
        
        btncancel = gtk.Button()
        cancelbox = gtk.VBox(False)
        btncancel.add(cancelbox)
        iconlogout = gtk.Image()
        iconlogout.set_from_icon_name("gtk-cancel",gtk.ICON_SIZE_LARGE_TOOLBAR)
        cancelbox.pack_start(iconlogout, False,False)
        cancelbox.pack_start(gtk.Label("Cancel"),False,False)
        btncancel.connect("clicked",lambda w: gtk.main_quit())
        hbox4 = gtk.HBox()
        hbox4.pack_end(btncancel,False,False)
        hbox4.set_size_request(200,48)
        vbox.pack_start(hbox4)
        

        Voverframe.pack_start(vbox,False,False)
        Hoverframe.pack_start(Voverframe,False,False)

        self.window.add(Hoverframe)
        
        self.window.show_all()
        
if __name__ == "__main__":
    pypower()
    gtk.main()
```

Using gmessage:
```
#!/bin/bash

gmessage "Are you sure you want to shut down your computer?" -center -title "Take action" -font "Sans bold 10" -default "Cancel" -buttons "_Restart":1,"_Shut down":2,"_Cancel":3 >/dev/null 

case $? in
    3)
        echo "Exit";;
    1)
        dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot;;
    2)
        dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown;;
esac
```

These should all work, if not let me know.

Thanks again

---

### Post by dcstar on 2013-08-03
It is pointless using these commands as they are all basically using the underlying command shell items:

```
man shutdown
man init
```

Why unnecessarily use things provided for use by the graphical desktop when there are far simpler alternatives?

---

