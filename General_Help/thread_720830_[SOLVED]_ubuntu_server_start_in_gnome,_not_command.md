---
title: "[SOLVED] ubuntu server: start in gnome, not command line"
date: 2008-03-10
forum: General Help
---

### Post by snorkytheweasel on 2008-03-10
Although I've installed Ubuntu server (7.10)  several times, I don't recall this happening:

The login starts at a command line, rather than in gnome. 

How to I configure the system to start in gnome?

Way back when, in several distros, the command was startx.

This time, the startx error message is 
[B]cannot stst /etx/X11/X (No such file or directory), aborting.
xinit: Server error.[/B]

How to I compel Ubuntu to start in gnome?

---

### Post by taurus on 2008-03-10
If you installed the server version, you only get a commandline.  If you want Gnome, then you need to install ubuntu-desktop package.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg  <-- to configure X server for your machine
sudo /etc/init.d/gdm start
```

---

### Post by RedSquirrel on 2008-03-10
You might also want to look at the **gnome-core** package.

ubuntu-desktop will install OpenOffice and all that other stuff.

---

### Post by snorkytheweasel on 2008-03-11
That solved it! Thanks.

Actually, I experimented a bit....

sudo apt-get install ubuntu-desktop
became 
sudo apt-get install [COLOR="Red"]**k**[/COLOR]ubuntu-desktop

sudo /etc/init.d/gdm start
became
sudo /etc/init.d/**[COLOR="Red"]k[/COLOR]**dm start

Since I really wanted a more windows-like interface for my boss, who has a terminal case of Remonditis

---

