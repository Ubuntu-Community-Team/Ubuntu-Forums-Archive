---
title: "Ubuntu 17.04 Desktop: random temporary freezing"
date: 2017-09-20
forum: General Help
---

### Post by dengineer on 2017-09-20
Recent clean install Ubuntu 17.04 - experiencing apparently random and temporary freezes - no mouse or keyboard response - lasting a variable length of time (seconds to minutes) but always self-recovering. Seems to be independent of my activity (Firefox, ThUnderbird, Android Studio, Files, ...). Syslog covering latest follows.

```
douglas@douglas-HP-Compaq-dc5850-Small-Form-Factor:~$ tail -n 100 /var/log/syslog
Sep 20 20:05:09 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:05:09:0372 Gs  automatically prevented from changing origin on system/package/ubuntu-zesty-main/desktop/org.gnome.Calendar.desktop/* from ubuntu-zesty-main to ubuntu-zesty-updates-main!
Sep 20 20:05:09 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:05:09:0382 Gs  automatically prevented from changing origin on system/package/ubuntu-zesty-security-main/desktop/shotwell.desktop/* from ubuntu-zesty-security-main to ubuntu-zesty-updates-main!
Sep 20 20:05:09 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:05:09:0387 Gs  automatically prevented from changing origin on system/package/ubuntu-zesty-main/desktop/update-manager.desktop/* from ubuntu-zesty-main to ubuntu-zesty-updates-main!
Sep 20 20:05:09 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:05:09:0391 Gs  automatically prevented from changing origin on system/package/ubuntu-zesty-main/desktop/org.gnome.Software.desktop/* from ubuntu-zesty-main to ubuntu-zesty-updates-main!
Sep 20 20:05:09 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:05:09:0413 Gs  automatically prevented from changing origin on system/package/ubuntu-zesty-security-main/desktop/display-im6.q16.desktop/* from ubuntu-zesty-security-main to ubuntu-zesty-updates-main!
Sep 20 20:05:22 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1]: Started Daily apt download activities.
Sep 20 20:05:29 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus[702]: [system] Activating service name='com.ubuntu.SoftwareProperties' (using servicehelper)
Sep 20 20:05:30 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus[702]: [system] Successfully activated service 'com.ubuntu.SoftwareProperties'
Sep 20 20:05:31 douglas-HP-Compaq-dc5850-Small-Form-Factor software-proper[7144]: Connecting to session manager
Sep 20 20:05:42 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/62914980"
Sep 20 20:05:54 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/62916852"
Sep 20 20:05:56 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd-resolved[914]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 192.168.0.1.
Sep 20 20:07:19 douglas-HP-Compaq-dc5850-Small-Form-Factor polkit-gnome-au[1611]: GtkDialog mapped without a transient parent. This is discouraged.
Sep 20 20:07:19 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/29360131"
Sep 20 20:07:51 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus[702]: [system] Activating service name='org.debian.apt' (using servicehelper)
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon: INFO: Initializing daemon
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:53 AptDaemon [INFO]: Initializing daemon
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus[702]: [system] Successfully activated service 'org.debian.apt'
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon: INFO: UpdateCache() was called
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: /usr/lib/python3/dist-packages/aptdaemon/worker/pkworker.py:35: PyGIWarning: PackageKitGlib was imported without specifying a version first. Use gi.require_version('PackageKitGlib', '1.0') before import to ensure that the right version gets loaded.
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]:   from gi.repository import PackageKitGlib as pk
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:53 AptDaemon [INFO]: UpdateCache() was called
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:53 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:53 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:53 AptDaemon.Worker [INFO]: Processing transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:07:53 douglas-HP-Compaq-dc5850-Small-Form-Factor software-proper[7144]: GtkDialog mapped without a transient parent. This is discouraged.
Sep 20 20:07:54 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/62928069"
Sep 20 20:07:54 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon.Worker: INFO: Updating cache
Sep 20 20:07:54 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:07:54 AptDaemon.Worker [INFO]: Updating cache
Sep 20 20:08:18 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-software-service.desktop[1627]: 00:08:18:0660 As  no format specified in system/package/ubuntu-zesty-multiverse/desktop/mythtv-setup.desktop/*
Sep 20 20:08:18 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [51287.621715] gnome-software[1627]: segfault at fffffffffffffff0 ip 00007f0d28ac3327 sp 00007ffd14ba2ef8 error 5 in libappstream-glib.so.8.0.11[7f0d28aa2000+4d000]
Sep 20 20:08:19 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Starting Notification regarding a crash report...
Sep 20 20:08:20 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Started Notification regarding a crash report.
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:08:26 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/b8c4cf52f4574996b7bf77000a56a20e
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: es-mirrors.evowise.com - time: 0.12482309341430664
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: la-mirrors.evowise.com - time: 0.12782883644104004
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: ny-mirrors.evowise.com - time: 0.1417217254638672
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: ubuntu.mirror.rafal.ca - time: 0.14200234413146973
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: ro-mirrors.evowise.com - time: 0.1783585548400879
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: ubuntu.mirror.cambrium.nl - time: 0.56441330909729
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: mirror: mirror.transip.net - time: 0.5998225212097168
Sep 20 20:08:26 douglas-HP-Compaq-dc5850-Small-Form-Factor compiz[1513]: and the winner is: es-mirrors.evowise.com
Sep 20 20:09:42 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Starting Notification regarding a crash report...
Sep 20 20:09:42 douglas-HP-Compaq-dc5850-Small-Form-Factor update-notifier-crash[8031]: gnome-software
Sep 20 20:09:54 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/14680067"
Sep 20 20:15:56 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd-resolved[914]: Grace period over, resuming full feature set (UDP+EDNS0+DO+LARGE) for DNS server 192.168.0.1.
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: The canary thread is apparently starving. Taking action.
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoting known real-time threads.
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1585 of process 1501 (n/a).
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1584 of process 1501 (n/a).
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1501 of process 1501 (n/a).
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoted 3 threads.
Sep 20 20:17:02 douglas-HP-Compaq-dc5850-Small-Form-Factor CRON[8069]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 20:19:02 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon: INFO: Quitting due to inactivity
Sep 20 20:19:02 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:19:02 AptDaemon [INFO]: Quitting due to inactivity
Sep 20 20:19:02 douglas-HP-Compaq-dc5850-Small-Form-Factor org.debian.apt[702]: 20:19:02 AptDaemon [INFO]: Quitting was requested
Sep 20 20:19:02 douglas-HP-Compaq-dc5850-Small-Form-Factor AptDaemon: INFO: Quitting was requested
Sep 20 20:23:14 douglas-HP-Compaq-dc5850-Small-Form-Factor unity-panel-ser[1526]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' failed
Sep 20 20:23:14 douglas-HP-Compaq-dc5850-Small-Form-Factor unity-panel-ser[1526]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
Sep 20 20:23:17 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus-daemon[1059]: Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service'
Sep 20 20:23:17 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Starting GNOME Terminal Server...
Sep 20 20:23:17 douglas-HP-Compaq-dc5850-Small-Form-Factor dbus-daemon[1059]: Successfully activated service 'org.gnome.Terminal'
Sep 20 20:23:17 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Started GNOME Terminal Server.
Sep 20 20:24:53 douglas-HP-Compaq-dc5850-Small-Form-Factor zeitgeist-fts[1825]: Unable to get info on application://nautilus-autostart.desktop
Sep 20 20:24:54 douglas-HP-Compaq-dc5850-Small-Form-Factor hud-service[1733]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/62914692"
Sep 20 20:30:10 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52599.741857] usb 4-3: USB disconnect, device number 8
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.080060] usb 4-3: new low-speed USB device number 9 using ohci-pci
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.266962] usb 4-3: New USB device found, idVendor=046d, idProduct=c05a
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.266968] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.266972] usb 4-3: Product: USB Optical Mouse
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.266975] usb 4-3: Manufacturer: Logitech
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.276497] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/0003:046D:C05A.0009/input/input24
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor kernel: [52600.276965] hid-generic 0003:046D:C05A.0009: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:12.1-3/input0
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor mtp-probe: checking bus 4, device 9: "/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3"
Sep 20 20:30:11 douglas-HP-Compaq-dc5850-Small-Form-Factor mtp-probe: bus: 4, device: 9 was not an MTP device
Sep 20 20:35:10 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-session[1337]: gnome-session-binary[1337]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 20 20:35:10 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-session-binary[1337]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 20 20:35:21 douglas-HP-Compaq-dc5850-Small-Form-Factor unity-settings-[1317]: failed to turn the kbd backlight off: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.freedesktop.UPower.KbdBacklight' on object at path /org/freedesktop/UPower/KbdBacklight
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: The canary thread is apparently starving. Taking action.
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoting known real-time threads.
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1585 of process 1501 (n/a).
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1584 of process 1501 (n/a).
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1501 of process 1501 (n/a).
Sep 20 20:36:24 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoted 3 threads.
Sep 20 20:48:26 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1]: Time has been changed
Sep 20 20:48:26 douglas-HP-Compaq-dc5850-Small-Form-Factor systemd[1039]: Time has been changed
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: The canary thread is apparently starving. Taking action.
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoting known real-time threads.
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1585 of process 1501 (n/a).
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1584 of process 1501 (n/a).
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Successfully demoted thread 1501 of process 1501 (n/a).
Sep 20 21:13:15 douglas-HP-Compaq-dc5850-Small-Form-Factor rtkit-daemon[1502]: Demoted 3 threads.
Sep 20 21:17:01 douglas-HP-Compaq-dc5850-Small-Form-Factor CRON[8201]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 21:27:20 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-session[1337]: gnome-session-binary[1337]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 20 21:27:20 douglas-HP-Compaq-dc5850-Small-Form-Factor gnome-session-binary[1337]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 20 21:27:20 douglas-HP-Compaq-dc5850-Small-Form-Factor unity-panel-ser[1526]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
```

---

