---
title: "How do I set a different startup splash screen?"
date: 2007-03-31
forum: General Help
---

### Post by rainwalker on 2007-03-31
I noticed that there's a nice looking "ubuntu-smooth.png" in "/usr/share/pixmaps/splash", and I was wondering how to set it as the one that shows up after logging in. 

Also, if anyone knows, is it possible to change the icon used for the logout button? I found a cooler looking one that I want to use.

---

### Post by Ramses de Norre on 2007-03-31
```
gconf-editor /apps/gnome-session/options
``` and set splash_image to the path to the one you like to use. Or install *gnome-splashscreen-manager* and use that (does the same through a gui).

The icon is defined by your theme, probably in ~/.themes. So search for the logout button icon there and replace it by your own.

---

### Post by yabbadabbadont on 2007-03-31
```
/usr/share/pixmaps/splash $ ls -l
total 112
-rw-r--r-- 1 root root 35324 2006-08-02 09:00 gnome-splash.png
-rw-r--r-- 1 root root 71403 2006-05-30 03:48 ubuntu-slick.png
lrwxrwxrwx 1 root root    16 2007-03-27 23:07 ubuntu-splash.png -> ubuntu-slick.png

```
ubuntu-splash.png is the one used by default.  Notice that it is a symbolic link that is currently pointing to ubuntu-slick.png on my machine (Dapper).  Just change the symbolic link so that it points to the file you wish to use for your Gnome splash image.  For example, if I wanted to switch mine to gnome-splash.png instead, I would run:
```
sudo ln -sf gnome-splash.png ubuntu-splash.png
```

Edit: Doh!  Too slow.  :D

---

### Post by rainwalker on 2007-03-31
Okay, found what I'm looking for. 

Now my problem is converting the svg icon I want to use into a png...

---

### Post by rainwalker on 2007-03-31
THANK YOU! That was exactly what I was looking for  :D

---

### Post by Xanderfoxx on 2007-05-03
> **yabbadabbadont said:**
> Just change the symbolic link so that it points to the file you wish to use for your Gnome splash image.  For example, if I wanted to switch mine to gnome-splash.png instead, I would run:

```
sudo ln -sf gnome-splash.png ubuntu-splash.png
```

Excuse me, but how would I switch the link to a different folder?

For example, the Desktop? Somewhere I have permissions? (It would not let me copy a file to pixmaps/splash)

---

### Post by yabbadabbadont on 2007-05-04
> **maurin.alex@gmail.com said:**
> Excuse me, but how would I switch the link to a different folder?

For example, the Desktop? Somewhere I have permissions? (It would not let me copy a file to pixmaps/splash)

Use sudo to copy the file in a terminal window, or just use the full path to your file when you create the link like in my previous example:
```
sudo ln -sf /home/username/imagedirectory/mysplash.png /usr/share/pixmaps/splash/ubuntu-splash.png
```
There is also a graphical tool for configuring the splash screen:
```
Package: gnome-splashscreen-manager
State: not installed
Version: 0.2-5
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 156k
Depends: ruby (>= 1.8), ruby (< 1.9), libglade2-ruby (>= 0.12.0), libgconf2-ruby (>= 0.12.0)
Description: manage your GNOME splash screen images
 Gnome Splashscreen Manager is a tool for managing your GNOME splash screen images. It provides a nice image list with
 options to add, remove images and set one of them as an active splash screen image. 
 
 Homepage: http://www.miketech.net/gnome-art/

```

---

### Post by Xanderfoxx on 2007-05-26
[QUOTE=yabbadabbadont;2594130]Use sudo to copy the file in a terminal window, or just use the full path to your file when you create the link like in my previous example:
```
sudo ln -sf /home/username/imagedirectory/mysplash.png /usr/share/pixmaps/splash/ubuntu-splash.png
```
[QUOTE]

OK. Thanks a bunch, I should have a lot of fun with that, should I get the time.

---

