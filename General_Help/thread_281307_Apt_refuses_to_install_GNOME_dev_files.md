---
title: "Apt refuses to install GNOME dev files"
date: 2006-10-20
forum: General Help
---

### Post by zergberg on 2006-10-20
I'm trying to install libgnome-dev, libgnomeui-dev, and libpanelappletmm-2.6-dev, but when I do, apt gives me a multitude of errors like:
```
The following packages have unmet dependencies:
libgnomeui-dev: 
Depends: libgnome2-dev (>= 2.13.7) but it is not going to be installed
Depends: libbonoboui2-dev (>= 2.13.1) but it is not going to be installed
Depends: libgnomevfs2-dev (>= 2.8.4-2) but it is not going to be installed
```

Isn't the exact sort of thing (dependency hell woohoo!) apt is supposed to avoid?

---

### Post by taurus on 2006-10-20
Have you tried using synaptic?

---

### Post by zergberg on 2006-10-20
Same error, but in a pretty dialogue.

---

### Post by taurus on 2006-10-20
Okay, exactly what did you type at the prompt?  Not sure but maybe you need to enable both universe & multiverse in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by zergberg on 2006-10-20
Everything already was enabled. :(

---

### Post by taurus on 2006-10-20
Then exactly how did you install it with aptitude?

---

### Post by zergberg on 2006-10-20
sudo apt-get install libgnome-dev libgnomeui-dev libpanelappletmm-2.6-dev

Below is only thread I've found in reference to this sort of thing, but I don't have any of the "not going to be installed" packages on my system.
[http://www.ubuntuforums.org/archive/index.php/t-77438.html](http://www.ubuntuforums.org/archive/index.php/t-77438.html)

EDIT: I think I've found the problem:
```
The following packages have unmet dependencies:
libdbus-1-dev: Depends: libdbus-1-2 (= 0.60-6ubuntu8) but 0.62-bmp1ubuntu1 is to be installed
```

Unfortunately, removing I don't know how to get the other dbus on there without removing half my system :|

---

### Post by taurus on 2006-10-20
Try one at a time!!!

```

sudo aptitude update
sudo aptitude libgnome-dev

```

p.s.  And try to use aptitude if you can...

---

### Post by az on 2006-10-20
> **zergberg said:**
> Everything already was enabled. :(

Do you have mixed repositories (like Debian and Ubuntu or Dapper and Edgy)?

---

