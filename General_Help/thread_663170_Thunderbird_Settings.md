---
title: "Thunderbird Settings"
date: 2008-01-09
forum: General Help
---

### Post by sekinto on 2008-01-09
Just recently I switched from Ubuntu to Xubuntu. Anyway, I copied all the user folders to an external hard drive, now that I'm in Xubuntu I tried to replace my new .mozilla-thunderbird folder with my old one. Once I do that though and try to open Thunderbird it says there is already a Thunderbird process running when there really isn't. How do I fix this?

---

### Post by p_quarles on 2008-01-09
Run the following:
```
gedit .mozilla-thunderbird/profiles.ini
```
And change the "Path" value to the name of the *xyzq*.default folder that actually exists in the .mozilla-thunderbird directory. That should take care of things.

---

### Post by sekinto on 2008-01-09
But the folder and configuration file numbers already match.

---

### Post by p_quarles on 2008-01-09
Hmm. I know I fixed this exact same problem at some point, but I guess I don't remember the exact thing that worked. 

Try this (starting in your home folder):
```
mkdir tb-temp
cd tb-temp
cp -R ~/.mozilla-thunderbird/*xyzq*.default .
cd ~
mv .mozilla-thunderbird .thunderbird-bak
```
At this point, restarting Thunderbird should automatically generate a new configuration directory. Start it, then stop it, and run these:
```
cd .mozilla-thunderbird/*new-xyzq*.default
cp -R ~/.tb-temp ,
```
Now, Thunderbird should be able to read your old settings with the new installation (/me crosses fingers).

---

