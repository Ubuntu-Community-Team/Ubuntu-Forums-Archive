---
title: "pls help with clipboard manager"
date: 2008-02-25
forum: General Help
---

### Post by mmoalem on 2008-02-25
hi there was looking for a clipboard manager that stores the words in a user defined databases. I tried glipper and its limited as it discard prvious entries once a number of entries is reached.
I tried DDM from getdeb but i get an error:
> 
michel@ubuntugateway:~$ desktop-data-manager

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.14.1/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): Gdk-CRITICAL **: gdk_keymap_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.14.1/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): Gdk-CRITICAL **: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.14.1/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (/usr/lib/desktop-data-manager/DesktopDataManagerApplet.exe:11888 : CRITICAL **: egg_keymap_resolve_virtual_modifiers: assertion `GDK_IS_KEYMAP (keymap)' failed




i tried klipper and i get this error:
> 
michel@ubuntugateway:~$ klipper
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/michel/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/michel/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file



anyone can make head or tail of this output? any other utility that will do the job?

cheers
michel

---

### Post by mmoalem on 2008-02-25
well... sorted porblem 2 with klipper - needed to change permissions on /.kde to allow everyone modify files - why should this be so compliacted only the linux gods know... 
but it doesnt do the job as i cant seem to assign a permanent list of words to stay for ever...
still working on ddm but if you have any idea of another app please advise

---

