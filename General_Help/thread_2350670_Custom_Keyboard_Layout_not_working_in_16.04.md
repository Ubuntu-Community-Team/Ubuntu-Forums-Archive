---
title: "Custom Keyboard Layout not working in 16.04"
date: 2017-01-26
forum: General Help
---

### Post by jf-moniquelevi on 2017-01-26
Hi All,
I finally upgraded my laptop from 14.04 to 16.04 (Gnome). Actually a clean install.
The custom keyboard layout doesn't work anymore.
It is a modified US layout.
I edited the  /usr/share/X11/xkb/symbols/us.
I ran 
```
sudo dpkg-reconfigure xkb-data
```
Well, nothing happened, the mods I had painstakingly done on /usr/share/X11/xkb/symbols/us had disappeared, the file had reverted to it's initial form. 
Fortunately, I had saved it !  Had been on Ubuntu since Dapper-Drake, learned a few tricks (not enough) !

There no " *.xkm files in /var/lib/xkb " to delete.

Obviously there is an operation to make the changes "stick" that I don't know.

Help !!!!
Thanks

---

