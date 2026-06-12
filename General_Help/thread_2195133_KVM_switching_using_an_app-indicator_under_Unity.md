---
title: "KVM switching using an app-indicator under Unity"
date: 2013-12-22
forum: General Help
---

### Post by madnordski on 2013-12-22
Problem: KVM hot-keys for switching monitor from Ubuntu 13 to another system when scroll-lock + scroll-lock did not work.

There are other solutions to this problem but what is posted here is a solution that adds an app-indicator which can be used to switch monitors.  The app-indicator is written in Python.  Save the file, make it executable (i.e. chmod +x file) and add it to your login startup under ubuntu 13+ using the Startup Applications program (search for startup using dash).  This is all new to me so posts which improve on this are welcome. :p

Conceded: putting the commands behind a custom hot-key sequence is probably a better solution.

The use of an app-indicator is a alternative which is self-revealing.

The program is attached to a reply to this message.  Use the attachment because Python needs the indentation and the forum appears to strip it out.

---

### Post by madnordski on 2013-12-22
Attempting to paste the program to restore indentation.  Managed to attach it after seeing that the fixed font does nothing.
--joe

[FONT=Fixedsys]
#!/usr/bin/env python

'''
  This app indicator switches a KVM from Ubuntu to another system.
  Install this app in Ubuntu 13.* using the instructions found here:
  [https://unity.ubuntu.com/projects/appindicators/](https://unity.ubuntu.com/projects/appindicators/)

  Copyright 2013 Joe King
  Authors: Joe King <jking @ mailbag . com>

  This program is free software: you can redistribute it and/or modify it
  under the terms of either or both of the following licenses:
 
  1) the GNU Lesser General Public License version 3, as published by the
  Free Software Foundation; and/or
  2) the GNU Lesser General Public License version 2.1, as published by
  the Free Software Foundation.
 
  This program is distributed in the hope that it will be useful, but
  WITHOUT ANY WARRANTY; without even the implied warranties of
  MERCHANTABILITY, SATISFACTORY QUALITY or FITNESS FOR A PARTICULAR
  PURPOSE.  See the applicable version of the GNU Lesser General Public
  License for more details.
 
  You should have received a copy of both the GNU Lesser General Public
  License version 3 and version 2.1 along with this program.  If not, see
  <http://www.gnu.org/licenses>
 '''
 
import gobject
import gtk
import appindicator
from os import system

'''
  Only two menu actions:
    1. toggle the KVM (switch to the other system)
    2. exit the app (for updating and the like)

  Change toggle as needed to support the keys your KVM uses.
'''

def toggle(w, buf):
  system("xset -led named \"Scroll Lock\"; sleep 1; xset led named \"Scroll Lock\"; xset -led named \"Scroll Lock\"")
 
def exitIndicator(w, buf):
  exit();

# the main thing

if __name__ == "__main__":
  ind = appindicator.Indicator("switch-to-pc-client",
                              "nm-adhoc",
                              appindicator.CATEGORY_APPLICATION_STATUS)
  ind.set_status(appindicator.STATUS_ACTIVE)
  ind.set_attention_icon("nm-adhoc")
 
  # create a menu
  menu = gtk.Menu()
 
  # define switch
  switch = "Switch to PC"
  menuItems = gtk.MenuItem(switch)
  menu.append(menuItems)
  menuItems.connect("activate", toggle, switch)
  menuItems.show()

  # define exit
  iExit = "Exit"
  menuItems = gtk.MenuItem(iExit)
  menu.append(menuItems)
  menuItems.connect("activate", exitIndicator, iExit)
  menuItems.show()

  ind.set_menu(menu)
 
  # give this thread to the gtk
  gtk.main()

[/FONT]

---

