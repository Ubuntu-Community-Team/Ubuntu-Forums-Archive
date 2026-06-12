---
title: "just installed server edt. how do I start x?"
date: 2006-10-04
forum: General Help
---

### Post by slimdog360 on 2006-10-04
I just done a server install and then downloaded xserver, gdm and kde-core. I still cant start X for some reason.
Ive tried all of the following commands

```
sudo /etc/init.d/gdm start
```
```
sudo update-rc.d -f gdm defaults
```
```
gmd
```
```
startx
```

and none work. Any help? thanks

---

### Post by ed_agamemnon on 2006-10-04
> ```
gmd
```

gdm?

---

### Post by slimdog360 on 2006-10-04
yeah, thats what I meant.

---

### Post by catanzag on 2006-10-04
Which kind of errors are given on the command line for every commands you quoted? and what about the X log output in /var/log?

regards

---

### Post by slimdog360 on 2006-10-04
it just says command not found.

---

### Post by catanzag on 2006-10-04
really strange, that is /etc/init.d/gdm is not present in your system; when you installed the package, currently gdm_2.14.6-0ubuntu2.1 (either via *dpkg -i* or via *apt-get install*, I don't know what did you use), had you got any errors/warnings? can you try to reinstall it to check that is OK?

---

### Post by slimdog360 on 2006-10-05
yay, I got it working. I had to install some fonts and I installed gdm rather then kdm for kde (derr). Worked nicely after that. I now have a completely blank canvas for me to work on.

---

### Post by kerry_s on 2006-10-05
On your next install do x-window-system-core and it will install everything for X.

Example:
sudo apt-get install x-window-system-core xterm (xdm,wdm,gdm,kdm) (fluxbox,icewm,blackbox,wmaker,kde-core,gnome-core,...)

---

