---
title: "User can't log in, but other users can"
date: 2012-10-22
forum: General Help
---

### Post by Superdude_123 on 2012-10-22
So after upgrading to Ubuntu 12.04 going about things for a few weeks later, user A (which has an encrypted home folder) can't log in graphically after boot, but user B can log in graphically after boot. Ironically, if I ssh to the box, user A can log in.

The mother board has started to show some signs of wear (ethernet adapter has been failing, had to install a separate network card), and I wonder if this is the cause, or could it be the keyboard it self? 

When I run  sudo dpkg --configure -a, nothing shows up as problematic, and the system has all the updates installed.

Ideas?

---

### Post by ~LoKe on 2012-10-23
What happens when User A tries to log in?

---

### Post by Superdude_123 on 2012-10-23
The user can enter his password yet after hitting enter, the user is returned to the log in screen.

---

### Post by ~LoKe on 2012-10-23
> **Superdude_123 said:**
> The user can enter his password yet after hitting enter, the user is returned to the log in screen.

Can you get a hold of .xsession-errors from that user?
```
cat /home/$USER/.xsession-errors
```

---

### Post by Superdude_123 on 2012-10-23
Here's what I get 

 openConnection: connect: No such file or directory
cannot connect to brltty at :0
gnome-session[1936]: EggSMClient-WARNING: Desktop file '/home/paulette/.config/autostart/turboprint-monitor.desktop' has malformed Icon key 'tpapplet.png'(should not include extension)
gnome-session[1936]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "turboprint-monitor" (No such file or directory)

(vino-server:2051): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
08/10/2012 04:34:49 PM Autoprobing TCP port in (all) network interface
08/10/2012 04:34:49 PM Listening IPv6://[::]:5900
08/10/2012 04:34:49 PM Listening IPv4://0.0.0.0:5900
08/10/2012 04:34:49 PM Autoprobing selected port 5900
08/10/2012 04:34:49 PM Advertising security type: 'TLS' (18)
08/10/2012 04:34:49 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
08/10/2012 04:34:49 PM Listening IPv6://[::]:5900
08/10/2012 04:34:49 PM Listening IPv4://0.0.0.0:5900
08/10/2012 04:34:49 PM Clearing securityTypes
08/10/2012 04:34:49 PM Advertising security type: 'TLS' (18)
08/10/2012 04:34:49 PM Clearing securityTypes
08/10/2012 04:34:49 PM Advertising security type: 'TLS' (18)
08/10/2012 04:34:49 PM Advertising authentication type: 'No Authentication' (1)
08/10/2012 04:34:49 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
08/10/2012 04:34:49 PM Listening IPv6://[::]:5900
08/10/2012 04:34:49 PM Listening IPv4://0.0.0.0:5900
08/10/2012 04:34:49 PM Clearing securityTypes
08/10/2012 04:34:49 PM Clearing authTypes
08/10/2012 04:34:49 PM Advertising security type: 'TLS' (18)
08/10/2012 04:34:49 PM Advertising authentication type: 'VNC Authentication' (2)
08/10/2012 04:34:49 PM Clearing securityTypes
08/10/2012 04:34:49 PM Clearing authTypes
08/10/2012 04:34:49 PM Advertising security type: 'TLS' (18)
08/10/2012 04:34:49 PM Advertising authentication type: 'VNC Authentication' (2)
08/10/2012 04:34:49 PM Advertising security type: 'VNC Authentication' (2)

(vino-server:2051): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(vino-server:2051): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
failed to create drawable
failed to create drawable
** Message: applet now embedded in the notification area
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: Log level 16: STACK_OP_RAISE_ABOVE: sibling window 0x1c00001 not in stack
gtk printer
gtk printer
gtk printer
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
/usr/bin/checkbox-qt: line 26:  2376 I/O possible            python $CHECKBOX_SHARE/run "$@" $CHECKBOX_SHARE/configs/$(basename $0).ini
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
ERROR:root:free space check failed
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 762, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeCache.py", line 1167, in checkFreeSpace
    for (dir, size) in [(archivedir, self.requiredDownload),
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MyCache.py", line 98, in requiredDownload
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the firefox-globalmenu package. This might mean you need to manually fix this package.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1000004 (Desktop) with a timestamp of 0.  This shouldn't happen!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(evolution-alarm-notify:2270): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

(gnome-settings-daemon:2008): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:2008): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-applet:2047): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:2150): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-shell-calendar-server:2104): Gdk-WARNING **: gnome-shell-calendar-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(evolution-alarm-notify:2270): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-screensaver:2225): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(vino-server:2051): Gdk-WARNING **: vino-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:2296): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(deja-dup-monitor:2367): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.37 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2367): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.38 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2367): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.39 of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

** (zeitgeist-datahub:2226): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Window manager warning: Log level 16: gnome-shell: Fatal IO error 0 (Success) on X server :0.

---

