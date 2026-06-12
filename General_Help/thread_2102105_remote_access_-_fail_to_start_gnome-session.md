---
title: "remote access - fail to start gnome-session"
date: 2013-01-06
forum: General Help
---

### Post by satimis on 2013-01-06
Hi all,

Server
Ubuntu 12.04 desktop 64bit
openssh-server installed

Local PC
Ubuntu 12.04 desktop 64bit
openssh-client installed


$ ssh -X satimis@192.168.0.11
$ gnome-session > gnome-session

Warning```

** (gnome-settings-daemon:24731): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:24731): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
compiz (core) - Error: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Failed to play sound: Not available
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(gnome-settings-daemon:24731): keyboard-plugin-WARNING **: Failed to set the keyboard layouts: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized

** (gnome-settings-daemon:24731): WARNING **: Failed to connect context: Connection refused

(gnome-settings-daemon:24731): clipboard-plugin-WARNING **: Clipboard manager is already running.

(gnome-settings-daemon:24731): color-plugin-WARNING **: failed to create device: GDBus.Error:org.freedesktop.ColorManager.Failed: failed to obtain org.freedesktop.color-manager.create-device auth

(gnome-settings-daemon:24731): color-plugin-WARNING **: GDBus.Error:org.freedesktop.ColorManager.Failed: failed to obtain org.freedesktop.color-manager.create-profile auth

(gnome-settings-daemon:24731): color-plugin-WARNING **: no xrandr-Philips Consumer Electronics Company-Philips 200W-BZ1063822605 device found: Failed to find output xrandr-Philips Consumer Electronics Company-Philips 200W-BZ1063822605

** (gnome-settings-daemon:24731): WARNING **: Failed to connect context: Connection refused
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
^C** Message: PID 0 (we are 24763) sent signal 2, shutting down...


(gnome-settings-daemon:24731): color-plugin-WARNING **: failed to create device:
 GDBus.Error:org.freedesktop.ColorManager.Failed: failed to obtain org.freedeskt
op.color-manager.create-device auth

(gnome-settings-daemon:24731): color-plugin-WARNING **: GDBus.Error:org.free[0/42]
top.ColorManager.Failed: failed to obtain org.freedesktop.color-manager.create-p
rofile auth

(gnome-settings-daemon:24731): color-plugin-WARNING **: no xrandr-Philips Consum
er Electronics Company-Philips 200W-BZ1063822605 device found: Failed to find ou
tput xrandr-Philips Consumer Electronics Company-Philips 200W-BZ1063822605

** (gnome-settings-daemon:24731): WARNING **: Failed to connect context: Connect
ion refused
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
^C** Message: PID 0 (we are 24763) sent signal 2, shutting down...

satimis@localhost:~$ ** Message: PID 24763 (we are 24763) sent signal 15, shutti
ng down...

(nm-applet:24763): libappindicator-WARNING **: Unable to send signal for NewStat
us: The connection is closed
** Message: moving back from GtkStatusIcon to indicator

(nm-applet:24763): Gtk-CRITICAL **: gtk_status_icon_set_visible: assertion `GTK_
IS_STATUS_ICON (status_icon)' failed
^C

```


$ cat gnome-session ```

GNOME_KEYRING_CONTROL=/tmp/keyring-mfg24m
SSH_AUTH_SOCK=/tmp/keyring-mfg24m/ssh
GNOME_KEYRING_PID=24727
GNOME_KEYRING_CONTROL=/tmp/keyring-mfg24m
SSH_AUTH_SOCK=/tmp/keyring-mfg24m/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-mfg24m
SSH_AUTH_SOCK=/tmp/keyring-mfg24m/ssh
GPG_AGENT_INFO=/tmp/keyring-mfg24m/gpg:0:1
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

```

However I can start xterm

Please help.

B.R.
satimis

---

