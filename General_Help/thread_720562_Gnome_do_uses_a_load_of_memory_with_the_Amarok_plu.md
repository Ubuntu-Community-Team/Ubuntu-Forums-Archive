---
title: "Gnome do uses a load of memory with the Amarok plugin installed"
date: 2008-03-10
forum: General Help
---

### Post by jtreach on 2008-03-10
After installing the amarok plugin for gnome-do whenever I start gnome-do it uses a load of memory (600mb of my 1gb) and doesn't work. Can this be fixed? I'm using Mysql for amarok.

Thanks in advance.

---

### Post by abhiroopb on 2008-03-10
same problem here, i guess its just buggy.

---

### Post by abhiroopb on 2008-03-10
apparently the problem is the mysql database:

[http://groups.google.com/group/gnome-do/browse_thread/thread/5728134c6d8d545c/c58793ecf0b8fc72?lnk=raot&safe=off](http://groups.google.com/group/gnome-do/browse_thread/thread/5728134c6d8d545c/c58793ecf0b8fc72?lnk=raot&safe=off)

Did a bit of digging:

basically the original .dll file is the one that is up for download (made 24-01-08).

Unfortunately the guy whose been making the amarok plugin has changed it quite a bit and the latest file which supports mysql does not seem to be uploaded.

More info:
[https://code.launchpad.net/~bcl1713/do/plugins-amarok](https://code.launchpad.net/~bcl1713/do/plugins-amarok)

any help on how to modify would be helpful.

---

### Post by jtreach on 2008-03-11
OKay thanks, that's some nice information! Lets hope someone knows what to do. :)

---

### Post by abhiroopb on 2008-03-11
Yea information is there, just not sure what to do with it!

---

### Post by davidsiegel on 2008-04-11
The Amarok plugin is completely buggy and unstable (it tends to go haywire and eat all of your memory especially if you use the mysql backend). DO NOT USE IT. It will be fixed in the future, but for now I strongly encourage you to remove it.

---

