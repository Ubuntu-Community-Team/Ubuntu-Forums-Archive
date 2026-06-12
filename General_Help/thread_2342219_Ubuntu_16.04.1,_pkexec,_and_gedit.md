---
title: "Ubuntu 16.04.1, pkexec, and gedit"
date: 2016-11-04
forum: General Help
---

### Post by xeddog on 2016-11-04
This is a fresh install of 16.04 desktop today.  When I went to try and use pkexec to start gedit as root, after the password prompt I get:

```
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(gedit:2047): Gtk-WARNING **: cannot open display: 

```

I am using pkexec because when using sudo or gksu I don't get the menu bar at the top of the window.  So how do I fix this, or is there another way to get root access with gedit (and nautilus btw)??


Thanks,

Wayne

---

### Post by wildmanne39 on 2016-11-04
The recommended way is to use:
```
sudo -H
```

---

### Post by xeddog on 2016-11-04
I tried that, but I still don't get the menu bar at the top for gedit.  


Wayne

---

### Post by mc4man on 2016-11-04
Install nautilus-admin package, restart nautilus or log out/in. 
Will be in context menu, Edit as Administrator for gedit, Open as Ad.. for nautilus.

---

### Post by xeddog on 2016-11-19
Sorry for the late reply, but nautilus-admin was already installed.  I cannot find the "as administrator" for neither gedit nor nautilus (now files).

Wayne

---

### Post by deadflowr on 2016-11-19
> **xeddog said:**
> Sorry for the late reply, but nautilus-admin was already installed.  I cannot find the "as administrator" for neither gedit nor nautilus (now files).

Wayne

Right Click within Files?
Right click on a folder and you should be seeing Open as Administrator.
Right click on a file and you should get edit as Administrator.
 Open as will ask for your password and then open a new window as root.
 Edit will ask for your password and open the file in the default text editor (gedit, normally; probably only, as I only use it with gedit anyway, so I do not know if it will use another editor if another is set as the default)

---

### Post by mc4man on 2016-11-19
> **xeddog said:**
> Sorry for the late reply, but nautilus-admin was already installed.  I cannot find the "as administrator" for neither gedit nor nautilus (now files).

Wayne
One would assume you've logged out or restarted in last 2 weeks but just checking as needed for extensions.
The package also installs a policy (/usr/share/polkit-1/actions/org.freedesktop.nautilus-admin.policy) so directly running thru pkexec should also work, does it?
Ex.'s
pkexec gedit
pkexec nautilus

---

### Post by xeddog on 2016-11-19
Mc4man - "pkexec gedit" and "pkexec nautilus" commands will launch the applications, but the menu at the top is missing.  This makes it a little difficult for many operations like find/replace for example.

Wayne

---

### Post by mc4man on 2016-11-19
> **xeddog said:**
> Mc4man - "pkexec gedit" and "pkexec nautilus" commands will launch the applications, but the menu at the top is missing.  This makes it a little difficult for many operations like find/replace for example.

Wayne
root versions of nautilus & gedit cannot use the global menu, menus should be in the app window.  You don't get that?
(- if not then what session, i.e., ubuntu or gnome or what Desktop, shown in 
```
echo $XDG_CURRENT_DESKTOP
```

---

