---
title: "X dies after login in"
date: 2013-09-29
forum: General Help
---

### Post by li_lau2 on 2013-09-29
After I login in successfully, the screen blanks and then returns to the login screen.
All this occurred after I updated my software two weeks ago, and I suspect that
something in the update is preventing X from starting properly (something about
root timing out and not being a registered authentication agent?).

I am not sure how to proceed from this point on, so any help would be
greatly appreciated.  Thanks.

Here is the .xsession-errors file:[INDENT]Script for cjkv started at run_im.[/INDENT]
[INDENT]Script for default started at run_im.[/INDENT]
[INDENT]Script for cjkv started at run_im.[/INDENT]
[INDENT]Script for default started at run_im.[/INDENT]
[INDENT]** Message: applet now removed from the notification area[/INDENT]
[INDENT]** Message: using fallback from indicator to GtkStatusIcon[/INDENT]
[INDENT]      JS LOG: IBus version is too old[/INDENT]
[INDENT]
[/INDENT]
[INDENT](nautilus:2366): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](nautilus:2366): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not get _NET_WORKAREA[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not determine workarea, guessing at layout[/INDENT]
[INDENT]      JS LOG: GNOME Shell started at Mon Sep 30 2013 10:36:31 GMT+0800 (HKT)[/INDENT]
[INDENT]failed to create drawable[/INDENT]
[INDENT]** Message: applet now embedded in the notification area[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not get _NET_WORKAREA[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (nautilus:2366): WARNING **: Can not determine workarea, guessing at layout[/INDENT]
[INDENT][2629:2654:0930/103652:ERROR: object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name[/INDENT]
[INDENT][2629:2654:0930/103652:ERROR: object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name[/INDENT]
[INDENT][2629:2629:0930/103652:ERROR: object_proxy.cc(532)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files[/INDENT]
[INDENT]WARNING:root:timeout reached, exiting[/INDENT]
[INDENT]PolicyKit daemon disconnected from the bus.[/INDENT]
[INDENT]We are no longer a registered authentication agent.[/INDENT]
[INDENT]Window manager warning: Log level 16: STACK_OP_RAISE_ABOVE: sibling window 0x2000027 not in stack[/INDENT]
[INDENT]Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.[/INDENT]
[INDENT]Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen![/INDENT]
[INDENT]PolicyKit daemon reconnected to bus.[/INDENT]
[INDENT]Attempting to re-register as an authentication agent.[/INDENT]
[INDENT]We are now a registered authentication agent.[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
(gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed[/INDENT]
[INDENT]gnome-session[2240]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed[/INDENT]
[INDENT]gnome-session[2240]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-shell:2361): GLib-GIO-WARNING **: Dropping signal ActiveSessionChanged of type (s) since the type from the expected interface is (o)[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-settings-daemon:2323): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT](nautilus:2366): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT](nm-applet:2368): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT](gnome-screensaver:2417): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT](update-notifier:2702): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Window manager warning: Log level 16: gnome-shell: Fatal IO error 0 (Success) on X server :0.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT]** (zeitgeist-datahub:2554): WARNING **: zeitgeist-datahub.vala:231: Unable to get name "org.gnome.zeitgeist.datahub" on the bus![/INDENT]
[INDENT]
[/INDENT]
[INDENT](deja-dup-monitor:2837): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.UDisks2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts[/INDENT]
[INDENT]
[/INDENT]
[INDENT](deja-dup-monitor:2837): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.MTPVolumeMonitor disconnected from the bus; removing drives/volumes/mounts[/INDENT]
[INDENT]
[/INDENT]
[INDENT](deja-dup-monitor:2837): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts[/INDENT]
[INDENT]
[/INDENT]
[INDENT](deja-dup-monitor:2837): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts[/INDENT]
[INDENT]
[/INDENT]

---

### Post by Impavidus on 2013-09-30
Have you checked the ownership of the files **.xsession-errors** and **.Xauthority**? Sometimes they get root-owned. You should be able to fix it by logging on to a console (ctrl-alt-F1).

---

### Post by li_lau2 on 2013-09-30
> **Impavidus said:**
> Have you checked the ownership of the files **.xsession-errors** and **.Xauthority**? Sometimes they get root-owned. You should be able to fix it by logging on to a console (ctrl-alt-F1).

Got it.  Thanks.

---

