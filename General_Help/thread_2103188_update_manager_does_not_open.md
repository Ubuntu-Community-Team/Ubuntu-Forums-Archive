---
title: "update manager does not open"
date: 2013-01-09
forum: General Help
---

### Post by tc101 on 2013-01-09
I am running 12.04.  When I click the update manager icon, nothing happens.  When I hit alt-tab to see everything that is open, the update manager icon shows up, but I can not actually open it.

---

### Post by ibjsb4 on 2013-01-09
```
sudo apt-get update
```

Then try your update manager

---

### Post by tc101 on 2013-01-10
No.  Same problem.  I click the icon, but nothing happens.

---

### Post by ibjsb4 on 2013-01-10
Try opening update manager in terminal.  Get any errors?

```
update-manager
```

Also could try reinstalling.

```
sudo apt-get install --reinstall update-manager update-manager-core
```

Have you added any PPA's recently?

---

### Post by tc101 on 2013-01-10
I entered "update-manager" in the terminal, and below is what I got:



tom@tom-OptiPlex-755:~$ update-manager

(update-manager:2191): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:2191): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
^Cdebconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

---

### Post by tc101 on 2013-01-10
I did the reinstall and now it is working.  Thanks for your help.

How do I get the update manager icon back ?

---

### Post by ibjsb4 on 2013-01-10
Don't know how thats done in Unity, maybe a reboot?

---

