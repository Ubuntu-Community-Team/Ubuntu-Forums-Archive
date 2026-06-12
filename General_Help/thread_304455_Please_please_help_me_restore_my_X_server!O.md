---
title: "Please please help me restore my X server!:O"
date: 2006-11-21
forum: General Help
---

### Post by gejr on 2006-11-21
Ok, I'm in trouble.. ubuntu won't bootup in any of the sessions. Neither Default, Gnome session, nor  Beryl works. Im in failsafe gnome now. It works.

Im not sure what I've done to cause this. I was trying to make beryl work in xfce4 and now i'm stuck with nothing. The loader crashes at the splash screen in every available session. It says "Loading window manager" and then it freezes. 

When i get into failsafe gnome i get an error saying 

> There was an error starting the GNOME Settings daemon.

Some things such as themes, sounds, or background settings may not work correctly.

The last error message was: 

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

Please help me...i don't know how to solve this. Any tips will be greatly appreciated. I tried sudo apt-get remove gnome-desktop-environment and then reinstalled it, but it didn't change anything.

-Gejr

---

### Post by idrinkwhisky on 2006-11-21
hi,

have you tried to reinstall your graphics card drivers from command line?

goodluck

---

### Post by drphilngood on 2006-11-22
I would try reinstalling the dbus packages.

edit:
I´ve found several Beryl users with HAL/dbus problems.
Try this:
```
sudo /etc/ini.d/dbus restart
```
if that works, then try uninstalling Beryl.

---

### Post by ciscosurfer on 2006-11-22
This link may be of assistance: [http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

---

### Post by gejr on 2006-11-23
Thanks guys, but I ended up reinstalling. I had removed basically anything worth saving on the computer anyway. Now I'll be more careful. It's a pain not knowing how to restore stuff when I mess things up, but I guess that's the way to learn. Have reinstalled ubuntu 4 times now, in 2 months..not bad. :)

---

