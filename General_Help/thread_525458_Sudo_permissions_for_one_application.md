---
title: "Sudo permissions for one application"
date: 2007-08-14
forum: General Help
---

### Post by ThinkBuntu on 2007-08-14
I've added this entry to my sudoers file:
```
myusername ALL=NOPASSWD: /usr/sbin/firestarter

```
So that I can make Firestarter launch with new sessions, but for some reason it doesn't. If I enter the command:
```
$ sudo firestarter

```
or
```
$ sudo /usr/sbin/firestarter

```
I'm still asked for a password.

What gives?

---

### Post by zvacet on 2007-08-14
[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html]("http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html")

---

### Post by kerry_s on 2007-08-14
sudo is picky like that. :)

%firestarter ALL=(root) NOPASSWD: /usr/sbin/firestarter

sudo addgroup firestarter
sudo gedit /etc/group

add your user to the firestarter group
example:
firestarter: xxxx:you

---

### Post by ThinkBuntu on 2007-08-14
> **zvacet said:**
> [http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html]("http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html")
Thanks for the link...but the entry suggested in the article for my Sudoers file is identical to the line I quoted in my post. Why does this setting not work?

---

### Post by ThinkBuntu on 2007-08-14
> **kerry_s said:**
> sudo is picky like that. :)

%firestarter ALL=(root) NOPASSWD: /usr/sbin/firestarter

sudo addgroup firestarter
sudo gedit /etc/group

add your user to the firestarter group
example:
firestarter: xxxx:you
A new group just for this app? Never thought of that, but thanks for the tip. I'll let you know if it works.

---

### Post by ThinkBuntu on 2007-08-14
Also, correct me if I'm wrong, but couldn't I just use:

```
sudo gpasswd -a myusername firestarter
```

to add myself to the group?

---

### Post by ThinkBuntu on 2007-08-14
Actually, even odder, I get a "Permission Denied" when trying to use gpasswd in Ubuntu with sudo! Bizarre...

So I'm going against the wishes of Ubuntu security and have added a root account, with which I had no problem using gpasswd...

---

