---
title: "Gnome-main-menu"
date: 2017-02-12
forum: General Help
---

### Post by sam_uk on 2017-02-12
For years i've been running gnome-main-menu 

It's a slab menu you can edit [https://launchpad.net/ubuntu/+source/gnome-main-menu](https://launchpad.net/ubuntu/+source/gnome-main-menu)

I've just upgraded to 16.10 and can't get it working.

Compiling [https://github.com/GNOME/gnome-main-menu](https://github.com/GNOME/gnome-main-menu) gives:

configure: error: Package requirements ( glib-2.0 >= 2.16.0			gio-2.0 >= 2.16.0 			gio-unix-2.0				gobject-2.0 					gtk+-2.0 >= 2.18 		gdk-2.0						libslab >= 1.5.2 mate-desktop-2.0 unique-1.0 ) were not met:

No package 'libslab' found
No package 'mate-desktop-2.0' found
No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables APPLICATION_BROWSER_CFLAGS
and APPLICATION_BROWSER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
user@user-thinkpad-x201:~/gnome-main-menu-master$ sudo apt-get install mate-desktop-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mate-desktop-2.0
E: Couldn't find any package by glob 'mate-desktop-2.0'
E: Couldn't find any package by regex 'mate-desktop-2.0'
user@user-thinkpad-x201:~/gnome-main-menu-master$ sudo apt-get install unique-1.0

Any suggestions or should I move over to Mint who have a similar menu app?

---

### Post by Perfect Storm on 2017-02-12
Try with:
```
sudo apt-get install libmate-desktop-2-17
```

---

### Post by sam_uk on 2017-02-12
Thanks, but already installed

libmate-desktop-2-17 is already the newest version (1.16.0-1).

Any other idea's?

---

### Post by Perfect Storm on 2017-02-12
If you're compiling you properly need the -dev version of mate:
```
sudo apt-get install libmate-desktop-dev
```

---

### Post by sam_uk on 2017-02-12
This works for me [https://launchpad.net/ubuntu/+source/mate-menu](https://launchpad.net/ubuntu/+source/mate-menu)

A change of menu, but hey ho it's basically what I want

[http://linuxscoop.com/wp-content/uploads/2015/12/Linux-Mint-17.3-MATE-Menu-Applications.jpg](http://linuxscoop.com/wp-content/uploads/2015/12/Linux-Mint-17.3-MATE-Menu-Applications.jpg)

---

