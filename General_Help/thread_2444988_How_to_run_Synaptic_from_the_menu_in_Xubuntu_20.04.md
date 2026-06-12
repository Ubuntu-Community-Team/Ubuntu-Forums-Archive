---
title: "How to run Synaptic from the menu in Xubuntu 20.04 Focal Fossa (Tip)"
date: 2020-06-07
forum: General Help
---

### Post by lambdafox on 2020-06-07
After installing synaptic, it does not run from the menu.  1) Find synaptic in the menu and right-click on it  2) choose Edit 3) change the command box from:         synaptics-pkexec    to:        sudo synaptic 4) tick the box to open in terminal  All you do in the terminal is enter your password and hit enter.  This is almost as easy as gksu used to be, just uglier!   I like LillyTerm; so I installed it and set it to my default terminal.  When I click on Synaptic in the menu, LillyTerm launches as usual.  That is to say it seems to ignore / not receive "sudo synaptic" from the menu.

---

### Post by #&amp;thj^% on 2020-06-07
It sounds as if you have found your own solution, but more below.
I myself do not have this problem with just an XFCE environment, if you are using any wayland dependent DE's IE: Gnome (For just one example)
This is a "feature" of Wayland, which prevents GUI software needing root from running via sudo. You can get around it by running
```
xhost +si:localuser:root
```
If this works for **"your particular problem" **then this will only last for the current session.
If the need arises to revert during the same session use:
```
xhost -si:localuser:root
```
Almost forgot, check and see if "policykit-1" is installed.
Information:
> PolicyKit is an application-level toolkit for defining and handling the policy
 that allows unprivileged processes to speak to privileged processes.
 .
 It is a framework for centralizing the decision making process with respect to
 granting access to privileged operations for unprivileged (desktop)
 applications.

---

### Post by pqwoerituytrueiwoq on 2020-06-07
works for me xubuntu 20.04 upgraded from 18.04 (both the whiskers menu and applications menus work)
```

~$ cat /usr/share/applications/synaptic.desktop 
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=synaptic-pkexec
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
X-Ubuntu-Gettext-Domain=synaptic
StartupNotify=true
StartupWMClass=synaptic
```

---

### Post by #&amp;thj^% on 2020-06-07
> **pqwoerituytrueiwoq said:**
> works for me xubuntu 20.04 upgraded from 18.04 (both the whiskers menu and applications menus work)


Thanks for the confirmation pqwoerituytrueiwoq, very helpful here. :D
I "suspect" wayland protocols or the like here.
@pqwoerituytrueiwoq could/would you please also show this:
```
apt policy policykit-1
```

---

### Post by pqwoerituytrueiwoq on 2020-06-07
```

$ apt policy policykit-1
policykit-1:
  Installed: 0.105-26ubuntu1
  Candidate: 0.105-26ubuntu1
  Version table:
 *** 0.105-26ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
$ apt-cache policy waylan*
wayland-scanner++:
  Installed: (none)
  Candidate: 0.2.5-2build1
  Version table:
     0.2.5-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
wayland-protocols:
  Installed: 1.20-1
  Candidate: 1.20-1
  Version table:
 *** 1.20-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu focal/main i386 Packages
        100 /var/lib/dpkg/status
waylandpp-dev:
  Installed: (none)
  Candidate: 0.2.5-2build1
  Version table:
     0.2.5-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
$ apt-cache policy xorg
xorg:
  Installed: 1:7.7+19ubuntu14
  Candidate: 1:7.7+19ubuntu14
  Version table:
 *** 1:7.7+19ubuntu14 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by #&amp;thj^% on 2020-06-07
> **pqwoerituytrueiwoq said:**
> ```

$ apt policy policykit-1
policykit-1:
  Installed: 0.105-26ubuntu1
  Candidate: 0.105-26ubuntu1
  Version table:
 *** 0.105-26ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
$ apt-cache policy waylan*
wayland-scanner++:
  Installed: (none)
  Candidate: 0.2.5-2build1
  Version table:
     0.2.5-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
wayland-protocols:
  Installed: 1.20-1
  Candidate: 1.20-1
  Version table:
 *** 1.20-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu focal/main i386 Packages
        100 /var/lib/dpkg/status
waylandpp-dev:
  Installed: (none)
  Candidate: 0.2.5-2build1
  Version table:
     0.2.5-2build1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
$ apt-cache policy xorg
xorg:
  Installed: 1:7.7+19ubuntu14
  Candidate: 1:7.7+19ubuntu14
  Version table:
 *** 1:7.7+19ubuntu14 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
```

Perfect, Thanks :)

---

### Post by lambdafox on 2020-06-07
i just checked and policykit-1 is installed

---

### Post by #&amp;thj^% on 2020-06-07
You may have to revert the changes you have made within the menu option, or better yet show us this from the terminal:
```
cat /usr/share/applications/synaptic.desktop
```

---

