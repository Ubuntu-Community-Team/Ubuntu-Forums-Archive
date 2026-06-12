---
title: "Synaptic and Add/Remove Broke"
date: 2008-01-23
forum: General Help
---

### Post by JimmyME on 2008-01-23
I can't open Synaptic or Add/Remove in Edgy because of the following error message:

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: Unable to lock the list directory

Here is the edgy-multiverse.list:

# automatically added by gnome-app-install on 2007-02-21 20:50:10.169984
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates

I would appreciate some help.  I buggered it up somehow but am not quite sure how.  I did do some poking around in system-admin-software sources

---

### Post by taurus on 2008-01-23
Open a terminal and edit /etc/apt/sources.list.d/edgy-multiverse.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```
and place a # in front of the last two lines to comment them out.  Save it and run then

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by JimmyME on 2008-01-23
Taurus,

Thanks, when I commented out the mutiverse then I got the same error with universe.list but applied your directions to that and it worked.

I appreciate it.

Jim

---

