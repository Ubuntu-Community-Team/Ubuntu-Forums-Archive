---
title: "dapper asked for password, edgy doesn't"
date: 2006-11-15
forum: General Help
---

### Post by angustia on 2006-11-15
hi,
i updated from dapper to edgy just two days after the 6.10 release date, and i have experience zero problems with it.

just yesterday i noticed that administration tools from the gnome menu are not asking for password at first time, while it always did it on dapper.

the only tools that keeps asking for password is synaptic.

is this something new i didn't know?

thanks in advance, and excuse my english

---

### Post by fragos on 2006-11-15
Not all tools under System-> Administration require a password.  As you noted, Synaptic is one that does.  Being administrative in nature and requiring root access are different things.

---

### Post by angustia on 2006-11-16
/usr/bin/shares-admin
/usr/bin/network-admin
/usr/bin/services-admin
/usr/bin/time-admin
/usr/bin/users-admin

those used to ask for password in dapper, so i spected the same on edgy...

also, it doesn't seem right that i could add or remove users without entering any password and without need of sudo.

---

### Post by fragos on 2006-11-16
Right you are.  I hadn't noticed because I just eneter my password when asked without thinking about why I've been asked.  These applications are read and execute by all.  If your concerned, perhaps you can change the permissions to only allow execution by root.

---

### Post by druhboruch on 2006-11-16
You should file a bug. (if it is not already filed...).

Thanks.  I didn't even notice it till now.

Your English is very good.

---

### Post by angustia on 2006-11-16
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946)

> Indeed this is due to the new architecture of gnome-system-tools in Edgy. The backend now is entirely separate, the frontend runs as normal user, and they communicate over dbus. The current dbus policy is to allow access to members of the admin group. Thus there is no sudo involved any more.

This drops the additional safeguards that gksudo provides, like verifying the person that is currently sitting on the computer (if there is no active sudo timestamp at least), although with physical access this merely provides a delay and does not stop any local attacks.

i don't know what to think about...

---

### Post by fragos on 2006-11-16
Any security system is as weak as it its least security conscious user.  all users, particularly privileged ones, should be responsible for logging off when leaving their computer.

---

