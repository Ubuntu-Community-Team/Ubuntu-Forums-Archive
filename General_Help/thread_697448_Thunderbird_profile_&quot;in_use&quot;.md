---
title: "Thunderbird profile &quot;in use&quot;?"
date: 2008-02-15
forum: General Help
---

### Post by 1002285 on 2008-02-15
I get an error message when starting Thunderbird that the profile is in use and therefore cannot be opened. I share this profile with Windows and in Windows it opens OK.
I tried starting it in Windows in the meantime, it opened there, and then again in Linux, and it is still "in use".

---

### Post by kellemes on 2008-02-15
Have this myself sometimes..
[http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

---

### Post by 1002285 on 2008-02-15
> **kellemes said:**
> Have this myself sometimes..
[http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

Thank you, the solution was there and I got the application to work.

---

### Post by drs305 on 2008-02-15
kellemes' link will most likely solve your problem. I run into this often enough that I've put a 'kill parent lock' script shortcut on the panel that seeks out and destroys all the parentlock and lock files on my computer. I use it a couple of times a week.

The main lines of the script are:
```
rm -f /<path-to-file/.parentlock
rm -f /<path-to-file/>parent.lock
rm -f /<path-to-file/>lock
```

The other way to do it is open firefox with profilemanager (firefox -profilemanager - for some reason firefox -p doesn't work for me in linux) and create a new profile pointing to the original user folders.

---

