---
title: "Error When Trying to Install Iceweasel"
date: 2007-06-20
forum: General Help
---

### Post by moore.bryan on 2007-06-20
[I]when i try to install the newest iceweasel, i get this:
```

moore@ubuntu:~$ sudo dpkg -i iceweasel_2.0.0.4-1_i386.deb
(Reading database ... 60475 files and directories currently installed.)
Unpacking iceweasel (from iceweasel_2.0.0.4-1_i386.deb) ...
dpkg: error processing iceweasel_2.0.0.4-1_i386.deb (--install):
 trying to overwrite `/usr/bin/firefox', which is also in package firefox
Errors were encountered while processing:
 iceweasel_2.0.0.4-1_i386.deb

```any ideas?
oh, and this even occurs after i rename /usr/bin/firefox to /usr/bin/firefox.old...
[/I]

---

### Post by moore.bryan on 2007-06-20
*no one using "the weez?"*

---

### Post by moore.bryan on 2007-06-23
*well, i was finally able to get this to work by forcing some packages and upgrading others through the debian unstable repos.  i'm really surprised no one in the community had anything to say about this...*

---

