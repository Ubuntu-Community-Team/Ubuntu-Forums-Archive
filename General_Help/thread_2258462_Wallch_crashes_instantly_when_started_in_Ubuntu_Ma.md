---
title: "Wallch crashes instantly when started in Ubuntu Mate 14.04?"
date: 2014-12-27
forum: General Help
---

### Post by William_Clark on 2014-12-27
I tried to install Wallch 4.12 in Ubuntu Mate 14.04 and it crashes instantly. I then pulled up the terminal to launch it to see what errors it made and this is what i got(sorry it is long)) could anyone help?
```

williamclarkonet@willdesktop:~$ wallch

(process:2467): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(process:2467): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(process:2467): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:2467): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_x11_display_get_xdisplay: assertion 'GDK_IS_DISPLAY (display)' failed

(process:2467): Gdk-CRITICAL **: IA__gdk_screen_get_number: assertion 'GDK_IS_SCREEN (screen)' failed
Segmentation fault (core dumped)
williamclarkonet@willdesktop:~$
```

---

### Post by tgalati4 on 2014-12-27
It looks like you installed something newer than what is in the repository:

> 
tgalati4@Mint17 ~/Desktop $ apt-cache search wallch
wallch - wallpaper changer
tgalati4@Mint17 ~/Desktop $ apt-cache policy wallch
wallch:
  Installed: (none)
  Candidate: 4.0-0ubuntu4
  Version table:
     4.0-0ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages


Remove what you installed and install what is in the standard, 14.04 Ubuntu repository:

```
sudo apt-get install wallch
```

---

### Post by William_Clark on 2014-12-28
thanks for the replay I have removed the previous wallch and installed from the  14.04 Ubuntu repository na dthe same thing is happening here is the terminal:

```
williamclarkonet@willdesktop:~$ sudo apt-get install wallch
[sudo] password for williamclarkonet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libkeybinder0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5webkit5 libqt5widgets5
  libxcb-icccm4 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0
The following NEW packages will be installed:
  libkeybinder0 libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5webkit5 libqt5widgets5
  libxcb-icccm4 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0 wallch
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.1 MB of archives.
After this operation, 70.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libqt5core5a:amd64.
(Reading database ... 259657 files and directories currently installed.)
Preparing to unpack .../libqt5core5a_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5core5a:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5dbus5:amd64.
Preparing to unpack .../libqt5dbus5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5dbus5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libxcb-icccm4:amd64.
Preparing to unpack .../libxcb-icccm4_0.4.1-1ubuntu1_amd64.deb ...
Unpacking libxcb-icccm4:amd64 (0.4.1-1ubuntu1) ...
Selecting previously unselected package libxcb-render-util0:amd64.
Preparing to unpack .../libxcb-render-util0_0.3.8-1.1ubuntu1_amd64.deb ...
Unpacking libxcb-render-util0:amd64 (0.3.8-1.1ubuntu1) ...
Selecting previously unselected package libxcb-xkb1:amd64.
Preparing to unpack .../libxcb-xkb1_1.10-2ubuntu1_amd64.deb ...
Unpacking libxcb-xkb1:amd64 (1.10-2ubuntu1) ...
Selecting previously unselected package libxkbcommon-x11-0:amd64.
Preparing to unpack .../libxkbcommon-x11-0_0.4.1-0ubuntu1_amd64.deb ...
Unpacking libxkbcommon-x11-0:amd64 (0.4.1-0ubuntu1) ...
Selecting previously unselected package libqt5gui5:amd64.
Preparing to unpack .../libqt5gui5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5gui5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5network5:amd64.
Preparing to unpack .../libqt5network5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5network5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5widgets5:amd64.
Preparing to unpack .../libqt5widgets5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5widgets5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5opengl5:amd64.
Preparing to unpack .../libqt5opengl5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5opengl5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5positioning5:amd64.
Preparing to unpack .../libqt5positioning5_5.2.1-1ubuntu2_amd64.deb ...
Unpacking libqt5positioning5:amd64 (5.2.1-1ubuntu2) ...
Selecting previously unselected package libqt5printsupport5:amd64.
Preparing to unpack .../libqt5printsupport5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5printsupport5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5qml5:amd64.
Preparing to unpack .../libqt5qml5_5.2.1-3ubuntu15.1_amd64.deb ...
Unpacking libqt5qml5:amd64 (5.2.1-3ubuntu15.1) ...
Selecting previously unselected package libqt5quick5:amd64.
Preparing to unpack .../libqt5quick5_5.2.1-3ubuntu15.1_amd64.deb ...
Unpacking libqt5quick5:amd64 (5.2.1-3ubuntu15.1) ...
Selecting previously unselected package libqt5sensors5:amd64.
Preparing to unpack .../libqt5sensors5_5.2.1+dfsg-2ubuntu2_amd64.deb ...
Unpacking libqt5sensors5:amd64 (5.2.1+dfsg-2ubuntu2) ...
Selecting previously unselected package libqt5sql5:amd64.
Preparing to unpack .../libqt5sql5_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5sql5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5sql5-sqlite:amd64.
Preparing to unpack .../libqt5sql5-sqlite_5.2.1+dfsg-1ubuntu14.2_amd64.deb ...
Unpacking libqt5sql5-sqlite:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Selecting previously unselected package libqt5webkit5:amd64.
Preparing to unpack .../libqt5webkit5_5.1.1-1ubuntu8_amd64.deb ...
Unpacking libqt5webkit5:amd64 (5.1.1-1ubuntu8) ...
Selecting previously unselected package libkeybinder0.
Preparing to unpack .../libkeybinder0_0.3.0-2_amd64.deb ...
Unpacking libkeybinder0 (0.3.0-2) ...
Selecting previously unselected package wallch.
Preparing to unpack .../wallch_4.0-0ubuntu4_amd64.deb ...
Unpacking wallch (4.0-0ubuntu4) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libqt5core5a:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5dbus5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libxcb-icccm4:amd64 (0.4.1-1ubuntu1) ...
Setting up libxcb-render-util0:amd64 (0.3.8-1.1ubuntu1) ...
Setting up libxcb-xkb1:amd64 (1.10-2ubuntu1) ...
Setting up libxkbcommon-x11-0:amd64 (0.4.1-0ubuntu1) ...
Setting up libqt5gui5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5network5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5widgets5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5opengl5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5positioning5:amd64 (5.2.1-1ubuntu2) ...
Setting up libqt5printsupport5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5qml5:amd64 (5.2.1-3ubuntu15.1) ...
Setting up libqt5quick5:amd64 (5.2.1-3ubuntu15.1) ...
Setting up libqt5sensors5:amd64 (5.2.1+dfsg-2ubuntu2) ...
Setting up libqt5sql5:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5sql5-sqlite:amd64 (5.2.1+dfsg-1ubuntu14.2) ...
Setting up libqt5webkit5:amd64 (5.1.1-1ubuntu8) ...
Setting up libkeybinder0 (0.3.0-2) ...
Setting up wallch (4.0-0ubuntu4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
williamclarkonet@willdesktop:~$ wallch
QEventLoop: Cannot be used without QApplication
QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Error: The message '--focus' could not be sent to Wallch.
Assuming that the previous Wallch instance crashed and starting a new one now. Sorry for this :)

(process:4815): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(process:4815): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(process:4815): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(process:4815): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_x11_display_get_xdisplay: assertion 'GDK_IS_DISPLAY (display)' failed

(process:4815): Gdk-CRITICAL **: IA__gdk_screen_get_number: assertion 'GDK_IS_SCREEN (screen)' failed
Segmentation fault (core dumped)
williamclarkonet@willdesktop:~$
```

---

### Post by tgalati4 on 2014-12-28
Well, it looks like *wallch* is not compatible with MATE, or you are missing a QT library (which would mean a dependency or packaging error).

Some other options:

[http://community.linuxmint.com/tutorial/view/997](http://community.linuxmint.com/tutorial/view/997)

[http://forums.linuxmint.com/viewtopic.php?f=219&t=162971](http://forums.linuxmint.com/viewtopic.php?f=219&t=162971)

---

### Post by William_Clark on 2014-12-28
Thanks for your help

---

