---
title: "wha hapind?"
date: 2006-08-11
forum: General Help
---

### Post by Roasted on 2006-08-11
I tried reinstalling wine, CS, and steam since I've had 4 days of constant bad luck. While trying to add the repository, after I reloaded I got this error. Does the repository get altered if you uninstall the programs that used that repository?

[IMG]http://i2.photobucket.com/albums/y36/Roasted/shit.png[/IMG]

---

### Post by meng on 2006-08-11
The message says you have duplicate entries. Check repository listing in Synaptic, or else check your /etc/apt/sources.list to see if you've entered the repositories twice. Not sure why that should cause problems with downloading/installing wine though, unless apt-get is supersensitive.

---

