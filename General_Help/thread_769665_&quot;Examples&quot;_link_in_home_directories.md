---
title: "&quot;Examples&quot; link in home directories"
date: 2008-04-26
forum: General Help
---

### Post by shthap3ns on 2008-04-26
Every time I create a new user with "useradd", the system adds an "examples" link into the users' home directory. I can't remove it. 

In the permissions, it says it is owned by root...I read here: [https://lists.ubuntu.com/archives/desktop-bugs/2006-October/059353.html](https://lists.ubuntu.com/archives/desktop-bugs/2006-October/059353.html)

Anyone know what's up?

---

### Post by ibuclaw on 2008-04-26
That seems rather odd. Mine have their permissions assigned to me, and I can't seem to change it to anyone else but me...

If you really don't want it. sudo rm it very carefully.
OR a safer way is to hit "**Alt+F2**" and type in:
```
gksu nautilus ~/
```
And you can now delete the Examples synlink from your user account.

If you want to remove it from every account you create in the future.
Again, "**Alt+F2**"
```
gksu nautils /etc/skel
```
And delete the Examples symlink in there too.

And you are sorted!

Regards
Iain

---

### Post by shthap3ns on 2008-04-26
Thanks! I've got it figured out now. It is a little weird though.

---

