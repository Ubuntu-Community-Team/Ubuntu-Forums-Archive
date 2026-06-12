---
title: "how do i make firefox my defualt browser"
date: 2006-08-13
forum: General Help
---

### Post by Polygon on 2006-08-13
it seems that ever since i installed opera (just for kicks) all the programs that use links,w hen i double click them, it ALWAYS opens in opera. i dont want this, i want them to open in firefox

how do i change it so that firefox is my defualt browser?

and yes in "preferred applications" its says firefox.

---

### Post by ciscosurfer on 2006-08-13
Go to Firefox's Edit Menu > Preferences > General "Tab" > Default Browser, and make sure it's checked.  

Likewise, try to find a similar setting in your Opera browser and "deselect" it as you don't want Opera to think that it's the default browser.

I hope that helps.  Don't know if that'll do it though.

---

### Post by mitch.c on 2006-08-13
Try:
```

sudo update-alternative --config gnome-www-browser

```
Make sure this is set to firefox. Then set your preferred application to (Custom):
```

gnome-www-browser %s

```
See if that does it.

---

### Post by ciscosurfer on 2006-08-13
This should be```
sudo update-alternatives --config gnome-www-browser
```

---

### Post by Polygon on 2006-08-13
the only thing in firefox is a button saying "check if firefox is the defualt browser" and i clicked that, and it doesnt seem to work or it doesnt do anything.

and in opera i cant find any options to change if opera is the defualt browser..

any other suggestions?

---

### Post by Polygon on 2006-08-13
```
mark@ubuntu:/$ sudo update-alternatives --config gnome-www-browser

There is only 1 program which provides gnome-www-browser
(/usr/bin/firefox). Nothing to configure.
mark@ubuntu:/$

```

hmm...

---

