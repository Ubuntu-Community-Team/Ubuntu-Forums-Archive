---
title: "Fresh gutsy install, no gnome, &quot;Unable to connect to dbus: Failed to connect to s...&quot;"
date: 2007-10-21
forum: General Help
---

### Post by pragmatick on 2007-10-21
Hi there,

after three failed installs of Ubuntu (I'll leave that for another time) I finally managed to actually boot Ubuntu. But whenever it starts, it says it can't start the gnome-settings-daemon. When I try to start it in the shell I get this:

** (gnome-settings-daemon:5975): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-O6YgEOoy64: Connection refused

(gnome-settings-daemon:5975): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-O6YgEOoy64: Connection refused

(gnome-settings-daemon:5975): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object

** (gnome-screensaver:5982): WARNING **: failed to register with the message bus
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192


The first time I startet Ubuntu the error message box actually said something about the dbus. I googled and found the advise to comment out everything regarding ipv6 in /etc/hosts. I did so, but it only helped removing the dbus line from the error box, the error itself is still the same.

If it helps, my Xorg.0.log: [http://pastebin.com/m3bf91ba9](http://pastebin.com/m3bf91ba9) and my dmesg output: [http://pastebin.com/m152928a0](http://pastebin.com/m152928a0) if it helps.

Thanks a lot in advance.

Simon

---

### Post by shinji2001xyz on 2008-02-15
See bug here: 
[https://bugs.launchpad.net/gnome-control-center/+bug/140469](https://bugs.launchpad.net/gnome-control-center/+bug/140469)

You may want to add gnome-settings-daemon in System>Prefs>Sessions.

cheers,
Syl.

---

