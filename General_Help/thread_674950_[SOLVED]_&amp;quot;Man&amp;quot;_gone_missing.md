---
title: "[SOLVED] &amp;quot;Man&amp;quot; gone missing"
date: 2008-01-22
forum: General Help
---

### Post by ChrisMP1 on 2008-01-22
For some reason, my 'man' program has dropped off the face of the earth.

```
$ man
bash: /usr/bin/man: No such file or directory
```

When I try to apt-get it, I get this:
```
# apt-get install man
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting man-db instead of man
man-db is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I tried to 'apt-get remove' it first, and then reinstall it, but I get the same thing. HELP!

---

### Post by ChrisMP1 on 2008-01-22
If I just decide to compile it from source, is there a way to tell apt that I have it installed?

---

### Post by p_quarles on 2008-01-22
> **ChrisMP1 said:**
> If I just decide to compile it from source, is there a way to tell apt that I have it installed?
You would need to get the "checkinstall" utility from the repositories. Then, you can use that instead of "make install":
```
sudo checkinstall
```
It will be made into a .deb package prior to installing it to the executable path.

The other thing to try, though, is to see if the package is broken:
```
sudo dpkg-reconfigure man-db
```

---

### Post by heindsight on 2008-01-22
/usr/bin/man is usually a symlink to /usr/lib/man-db/man (which is from the man-db package)
I can't imagine why /usr/bin/man would not be present, unless you accidentally deleted it (probably
without realising) or the man-db package is somehow broken.

Either way, assuming that man-db is not so badly broken that /usr/lib/man-db/man is also gone,
you can get /usr/bin/man back like so:
```
cd /usr/bin
sudo ln -s ../lib/man-db/man man
```

---

### Post by ChrisMP1 on 2008-01-22
Thanks for telling me about the symlink. Why on earth would an executable binary be installed under /lib?? Anyway, recreating the symlink worked. Also, thanks to p_quarles for telling me about checkinstall. That might come in handy!

---

