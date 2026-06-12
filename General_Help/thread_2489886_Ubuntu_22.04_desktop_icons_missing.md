---
title: "Ubuntu 22.04 desktop icons missing"
date: 2023-08-13
forum: General Help
---

### Post by patspiper on 2023-08-13
Hello,
Since a few days, and probably after some automatic update, my ubuntu 22.04 (wayland) stopped displaying desktop icons unless a logout/login is performed, or the desktop icons NG (DING) extension is disabled and reenabled (via the extensions app). Even right clicking the desktop shows a different menu when the icons aren't showing.

journalctl shows the following entries:
```
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: Detected async api for thumbnails
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:159:9
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: @/usr/share/gnome-shell/extensions/ding@rastersoft.com/ding.js:130:15
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: init@/usr/share/gnome-shell/extensions/ding@rastersoft.com/dbusUtils.js:896:34
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: getIntrospectionData@/usr/share/gnome-shell/extensions/ding@rastersoft.com/dbusUtils.js:388:126
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: _makeProxyWrapper/<@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:250:17
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: _injectToMethod/klass[method]@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:273:25
Aug 13 16:07:02 localpc gnome-shell[2291]: DING: (gjs:2903): Gjs-CRITICAL **: 16:07:02.103: JS ERROR: Gio.IOErrorEnum: Error calling StartServiceByName for org.gnome.Nautilus: Timeout was reached
```

It seems that DING isn't starting at all on boot.

Any idea about the cause and solution?

---

### Post by #&amp;thj^% on 2023-08-13
For your Desktop Icons, is this installed?
```
apt policy gnome-shell-extension-desktop-icons-ng
```
Logging out then back in should enable the extension.

---

### Post by patspiper on 2023-08-13
> **1fallen said:**
> For your Desktop Icons, is this installed?
```
apt policy gnome-shell-extension-desktop-icons-ng
```

It is installed (Desktop Icons NG is DING)
> **1fallen said:**
>  Logging out then back in should enable the extension.
This is what i had mentioned in my post above. But rebooting leads back to square one.

---

### Post by #&amp;thj^% on 2023-08-13
> **patspiper said:**
> 
This is what i had mentioned in my post above. But rebooting leads back to square one.

I saw that in your first post, are you sure they all load at boot?
```
gsettings get org.gnome.shell enabled-extensions
```
Would be a good start.

---

### Post by patspiper on 2023-08-13
gsettings get org.gnome.shell enabled-extensions(right upon reboot):
```
['user-theme@gnome-shell-extensions.gcampax.github.com', 'ubuntu-appindicators@ubuntu.com', 'ubuntu-dock@ubuntu.com', 'Move_Clock@rmy.pobox.com', 'tophat@fflewddur.github.io', 'ding@rastersoft.com']
```

---

### Post by #&amp;thj^% on 2023-08-13
Please try this, might just need a bump:
```
sudo apt install --reinstall gnome-shell-extension-desktop-icons-ng
##And
sudo apt install --reinstall gnome-shell-extension-prefs
```
The bottom line of the code is a tool to activate the any or all extensions using the Extensions tool.

---

### Post by patspiper on 2023-08-13
Reinstalling both didn't help

---

### Post by #&amp;thj^% on 2023-08-13
My friend this is the only other method I know for the missing Desktop Icons
```
sudo apt-get install --reinstall ubuntu-desktop
```
Save any open files or projects you might have running before.
Good luck

---

