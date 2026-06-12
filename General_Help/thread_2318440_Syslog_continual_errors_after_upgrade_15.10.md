---
title: "Syslog continual errors after upgrade 15.10"
date: 2016-03-26
forum: General Help
---

### Post by jhmaccuish on 2016-03-26
Hello,

After upgrading to 15.10 my computer is more laggy than it was before. The gnome-settings-daemon is constantly throwing a permission error. So much so that it is actually hard to read the system log directly as it is always scrolling on with new errors generated. Here is a small exert of the errors if anyone has any suggestion that would be appreciate:

 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 2 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): GLib-GIO-CRITICAL **: g_dbus_proxy_call_internal: assertion 'G_IS_DBUS_PROXY (proxy)' failed
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 276 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional org.freedesktop.Notifications[1105]: (notify-osd:1576): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 6 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional org.a11y.Bus[1105]: (process:1121): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional x-session-manager[1101]: dconf-CRITICAL: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: x-session-manager[1101]: dconf-CRITICAL: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 82 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional org.freedesktop.Notifications[1105]: (notify-osd:1576): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional org.a11y.Bus[1105]: (process:1121): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional x-session-manager[1101]: dconf-CRITICAL: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: x-session-manager[1101]: dconf-CRITICAL: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 18 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): GLib-GIO-CRITICAL **: g_dbus_proxy_call_internal: assertion 'G_IS_DBUS_PROXY (proxy)' failed
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: message repeated 2 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): GLib-GIO-CRITICAL **: g_dbus_proxy_call_internal: assertion 'G_IS_DBUS_PROXY (proxy)' failed
Mar 26 08:56:27 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:28 jamie-Gazelle-Professional gnome-session[1101]: message repeated 300 times: [ (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.]
Mar 26 08:56:28 jamie-Gazelle-Professional org.freedesktop.Notifications[1105]: (notify-osd:1576): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.
Mar 26 08:56:28 jamie-Gazelle-Professional gnome-session[1101]: (gnome-settings-daemon:1240): dconf-CRITICAL **: unable to create file '/home/jamie/.cache/dconf/user': Permission denied.  dconf will not work properly.

Thanks,

---

### Post by v3.xx on 2016-03-26
> After upgrading to 15.10 my computer is more laggy than it was before.

What are your computer specs?  In terminal, enter..

```
inxi -b
```

At first look, this looks like an upgrade gone bad.  Maybe the package manager can help.

```
sudo apt -f install
```

That will attempt to fix broken packages.

This permission problem with your home folder shouldn't be.  Your home should be owned by you the user.  You can check to see who is owner by right clicking on the file or folder and look at permissions.

Not much, but its a start :)

---

