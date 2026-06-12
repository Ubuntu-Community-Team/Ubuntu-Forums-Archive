---
title: "Ubuntu 14.04.1 LTS Wifi Dies out after Suspend"
date: 2014-10-14
forum: General Help
---

### Post by Nabz23 on 2014-10-14
Before I get started, yes I have googled this problem LOL, this one seems to be the one that works:
[http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi-connection](http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi-connection)

The code that helps alot of people is this:

```
sudo touch /etc/pm/sleep.d/wakenet.sh

sudo chmod +x /etc/pm/sleep.d/wakenet.sh

sudo gedit /etc/pm/sleep.d/wakenet.sh


Insert the following lines:
  #!/bin/bash case "$1" in thaw|resume) nmcli nm sleep false ;; *) ;; esac exit $? 
```

And then you save the gedit file.

When I do that I get this error:

```
(gedit:24243): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:24243): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


```

Anyone know how to get out of this problem? I have to always unplug my router its annoying because I need Ubuntu for school.

Thanks in advance

---

