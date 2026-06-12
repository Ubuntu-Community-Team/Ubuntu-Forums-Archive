---
title: "Couple problems with 12.10"
date: 2012-10-20
forum: General Help
---

### Post by ~LoKe on 2012-10-20
Haven't used Ubuntu for the past couple releases and just installed it again.  After some initial issues I've got it installed.

Now, however, sometimes my mouse doesn't work.  And it's strange, because I'm always able to click launchers in the Unity dock, as well as use Dash, but any time I want to click/right click the desktop, click on a button in a window, it doesn't work.  Completely unresponsive.  Right now, the mouse happens to work, but it's the OPPOSITE.  I can use it within the desktop space, but can't click any launchers...

Makes no sense to me.

Another problem is that if I move my cursor to the right side of the screen, it pops back onto the left.  No idea why this is.

---

### Post by dino99 on 2012-10-20
before answering, i've some questions:
- which kind of mouse is it ? is it plugged via usb or else ?
- which video driver is used ? on which card/chipset ?
- what says logs ? (.xsession-errors & /var/log/)

at first glance im thinking about a video driver issue, is it activated ?

---

### Post by ~LoKe on 2012-10-20
R.A.T. 7 Mouse.  It's detected perfectly and works in specific areas of the desktop.  If I log out/log back in, it fixes the issue so I'll just live with it.

Driver is 304.60, it's installed and recognized.  Card is nVidia 560ti.

> compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/n0c/.compiz/session/106f98049c2afbf9ee135078149395818000000020010032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
** Message: using fallback from indicator to GtkStatusIcon
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Power Button

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Video Bus

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Power Button

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Virtual core XTEST keyboard

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Virtual core XTEST pointer

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer

** (gnome-settings-daemon:2057): CRITICAL **: setup_bg: assertion `manager->priv->bg == NULL' failed
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Power Button

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Video Bus

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Power Button

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Virtual core XTEST keyboard

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device Virtual core XTEST pointer

(gnome-settings-daemon:2057): GLib-CRITICAL **: g_variant_get_boolean: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed
mouse-plugin-Message: checking on device AT Translated Set 2 keyboard
mouse-plugin-Message: checking on device Saitek Cyborg R.A.T.7 Mouse
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Video Bus
mouse-plugin-Message: checking on device Power Button
mouse-plugin-Message: checking on device Virtual core XTEST keyboard
mouse-plugin-Message: checking on device Virtual core XTEST pointer

** (gnome-settings-daemon:2057): CRITICAL **: setup_bg: assertion `manager->priv->bg == NULL' failed

(gnome-settings-daemon:2057): color-plugin-WARNING **: failed to reset xrandr-Goldstar Company Ltd-LG TV-16843009 gamma tables: gamma size is zero

(gnome-settings-daemon:2057): color-plugin-WARNING **: failed to reset xrandr-Goldstar Company Ltd-LG TV-16843009 gamma tables: gamma size is zero

(gnome-settings-daemon:2057): color-plugin-WARNING **: failed to reset xrandr-Goldstar Company Ltd-LG TV-16843009 gamma tables: gamma size is zero
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:2530): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

** (nautilus:2100): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2100): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

(update-notifier:2616): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(update-notifier:2616): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed

(update-notifier:2616): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:2057): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:2057): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-control-center:2612): info-cc-panel-WARNING **: Unable to get graphics info: Failed to execute child process "glxinfo" (No such file or directory)

** (firefox:2662): WARNING **: Failed to open webapp application path dir /usr/share/ubuntu/unity-webapps/userscripts: Error opening directory '/usr/share/ubuntu/unity-webapps/userscripts': No such file or directory

** (firefox:2662): WARNING **: Failed to open webapp application path dir /usr/share/gnome/unity-webapps/userscripts: Error opening directory '/usr/share/gnome/unity-webapps/userscripts': No such file or directory

** (firefox:2662): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory
gpg: /tmp/tmpnvmybn/trustdb.gpg: trustdb created

(gnome-settings-daemon:2057): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:2057): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
gnome-session[2001]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
gnome-session[2001]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed

(nm-applet:2092): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:2093): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:2094): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(telepathy-indicator:2513): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(deja-dup-monitor:2710): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.UDisks2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2710): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2710): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(nautilus:2100): Gdk-WARNING **: nautilus: Fatal IO error 0 (Success) on X server :0.


(update-notifier:2616): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

CRITICAL:__main__:Can't connect to dbus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-zTChEfguSg: Connection refused, fallback to direct connexion as a fallback:
WARNING:oneconf.hosts:Error in loading other_hosts file: [Errno 2] No such file or directory: '/home/n0c/.cache/oneconf/6391bada0e1c5b876ca817d050833f63/other_hosts'

---

### Post by 2F4U on 2012-10-21
The RAT 7 seems to be special and needs manual configuration:

[http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/](http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/)

---

### Post by ~LoKe on 2012-10-21
> **2F4U said:**
> The RAT 7 seems to be special and needs manual configuration:

[http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/](http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/)

Not sure how that could be the issue since it works fine if I log out and back in. Also works in select parts of the screen, so I'm blaming it on the OS itself.

---

### Post by ~LoKe on 2012-10-21
Formatted and installed 12.04.  Same exact problems.  Tried modifying xorg as described above, to no effect.

---

### Post by djwild on 2012-10-27
Hi,

I have the exact same problem as the OP. Sometimes after a while, I cannot click or scroll in some applications (firefox, vlc, etc.), but I can click on launchers. Closing the application and re-opening it woks sometimes. This is a fresh Ubunu 12.10 installation after a full HDD format. It used to work just fine in 12.04.

I have the open source Intel video driver running on an ivy bridge HD4000 GPU. I am using a USB wireless keyboard+mouse combo: Rapoo E2700.

Do you have any idea what the problem might be and where I should look for more details?

---

