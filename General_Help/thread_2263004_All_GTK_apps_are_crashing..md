---
title: "All GTK apps are crashing."
date: 2015-01-28
forum: General Help
---

### Post by iAmBerlo on 2015-01-28
I am running Ubuntu 14.04 with "xubuntu-desktop" installed as my desktop environment. There were updates this morning which I installed from the GUI that prompted on my screen. Since restarting my machine, every GTK app crashes as soon as I select any UI element. I'm not sure how I can provide error logs as a crash report doesn't even prompt on my screen, the app just closes. This is affecting Evolution Mail, Gnumeric, Abiword, etc.

---

### Post by ibjsb4 on 2015-01-30
Anything in /var/crash/?

Try opening an app in terminal, like abiword.
```
abiword
```
Get any errors?

Check for broken packages.
```
sudo apt-get -f install
```

Did you get a kernel upgrade?  Try going back to previous kernel.

---

### Post by iAmBerlo on 2015-02-02
I have done a complete reinstall, this time using Xubuntu instead of Ubuntu and then installing the xubuntu-desktop. I think this may have been my own fault, as I added in the Elementary OS Pantheon testing repos and installed Pantheon desktop environment. I haven't had any issues since the reinstall, but I appreciate your help.

---

