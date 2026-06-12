---
title: "Either can't update anymore or updater not deleting installed updates from list."
date: 2007-04-25
forum: General Help
---

### Post by Fireblend on 2007-04-25
Today I checked and there were 5 new updates, so I clicked on install, and it did seem to download the files, but when it was installing the window just closed and the list is still there, as if I hadn't installed anything.  Help? I'd like to update my system and get that annoying orange box out of my panel.

Thanks in advance

---

### Post by kpkeerthi on 2007-04-25
try from terminal and see what happens..
```
sudo aptitude update
```
and then..
```
sudo aptitude dist-upgrade
```

---

### Post by Fireblend on 2007-04-25
after dist-upgrade it says:

> The following packages will be upgraded:
  automatix2 gnome-panel gnome-panel-data libpanel-applet2-0 tzdata 
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2421kB of archives. After unpacking 28.7kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

### Post by Fireblend on 2007-04-25
Bump. Sorry but I really need help.

---

### Post by spankymasterc on 2007-04-25
try removing automatix Repositories and 

> 
sudo apt-get update

> sudo apt-get upgrade

automatix somethimes cant connect.....

---

### Post by Fireblend on 2007-04-25
It still won't work.

> dpkg: syntax error: unknown user `postfix' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:


---

