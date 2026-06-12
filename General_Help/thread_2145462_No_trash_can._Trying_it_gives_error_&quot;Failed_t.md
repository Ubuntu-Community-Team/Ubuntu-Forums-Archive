---
title: "No trash can. Trying it gives error &quot;Failed to connect to the Trash. Operation no...&quot;"
date: 2013-05-15
forum: General Help
---

### Post by J V on 2013-05-15
**To anyone that finds this problem**
I don't know what exactly the cause was, but installing gvfs and several reboots managed to magically fix the problem. If you find a definitive cause/fix feel free to add it here.

**Original post**
Hovering or clicking on the trash icon in my toolbar gives me the cheery message:
> Failed to connect to the Trash. Operation not supported

The icon doesn't show in thunar, but the trash folder exists at ~/.local/share/Trash. I deleted the  folders inside after the problem showed up and I needed to save space,  because my home partition managed to get itself completely filled up  right before the problem occurred - hints to the problem?

Considering my 34 day uptime might be the problem I rebooted but that didn't fix anything.

my /var/log/dpkg.log from just before the problem occured (note the upgrade of the desktop-file-utils package):
```
2013-05-15 18:23:59 startup archives unpack
2013-05-15 18:24:00 install baobab <none> 3.4.1-0ubuntu1
2013-05-15 18:24:00 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:00 status triggers-pending libglib2.0-0 2.32.3-0ubuntu1
2013-05-15 18:24:00 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:00 status triggers-pending libglib2.0-0:i386 2.32.3-0ubuntu1
2013-05-15 18:24:00 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:00 status triggers-pending man-db 2.6.1-2ubuntu1
2013-05-15 18:24:00 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:00 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-05-15 18:24:00 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:01 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-05-15 18:24:01 status half-installed baobab 3.4.1-0ubuntu1
2013-05-15 18:24:01 status unpacked baobab 3.4.1-0ubuntu1
2013-05-15 18:24:01 status unpacked baobab 3.4.1-0ubuntu1
2013-05-15 18:24:01 trigproc libglib2.0-0 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2013-05-15 18:24:01 status half-configured libglib2.0-0 2.32.3-0ubuntu1
2013-05-15 18:24:01 status installed libglib2.0-0 2.32.3-0ubuntu1
2013-05-15 18:24:01 trigproc libglib2.0-0:i386 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2013-05-15 18:24:01 status half-configured libglib2.0-0:i386 2.32.3-0ubuntu1
2013-05-15 18:24:01 status installed libglib2.0-0:i386 2.32.3-0ubuntu1
2013-05-15 18:24:01 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-05-15 18:24:01 status half-configured man-db 2.6.1-2ubuntu1
2013-05-15 18:24:01 status installed man-db 2.6.1-2ubuntu1
2013-05-15 18:24:01 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-05-15 18:24:01 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-05-15 18:24:01 status installed desktop-file-utils 0.20-0ubuntu3
2013-05-15 18:24:01 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-05-15 18:24:01 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-05-15 18:24:02 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-05-15 18:24:02 startup packages configure
2013-05-15 18:24:02 configure baobab 3.4.1-0ubuntu1 <none>
2013-05-15 18:24:02 status unpacked baobab 3.4.1-0ubuntu1
2013-05-15 18:24:02 status half-configured baobab 3.4.1-0ubuntu1
2013-05-15 18:24:02 status installed baobab 3.4.1-0ubuntu1
```

I then installed gvfs on a wild hunch (which went nowhere)

Would really appreciate any hints at all.

.xsession-errors tells me nothing that seems to have anything to do with the problem:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-RSt9cx/pkcs11: No such file or directory
Conky: /home/j/.conkyrc: 16: config file error
Conky: desktop window (35a) is root window
Conky: window type - normal
Conky: drawing to created window (0x1e00002)
Conky: drawing to double buffer

(polkit-gnome-authentication-agent-1:2894): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2894): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-RSt9cx/pkcs11: No such file or directory

(xfce4-indicator-plugin:2936): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
# And about 20 more lines of gtk errors
```

---

