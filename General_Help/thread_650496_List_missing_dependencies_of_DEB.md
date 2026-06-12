---
title: "List missing dependencies of DEB"
date: 2007-12-26
forum: General Help
---

### Post by rbt123 on 2007-12-26
Hi, when i try to install a file.deb from Ubuntu 6.06 dapper gui, it complains of a missing dependency. 
Actualy there's more than one missing dependecy, but it only list one.

How can i [COLOR="Blue"]get the list of missing dependecies[/COLOR] of the file.deb? I don't want to use "apt-get -install", i just want to [COLOR="Blue"]findout which dependencies are required[/COLOR] by the file.deb, [COLOR="Blue"]but is missing from my system[/COLOR].

Can dpkg-deb or dpkg perform these tasks?

Please help, thanks!

---

### Post by rbt123 on 2007-12-26
Anyone ?

---

### Post by artinla on 2007-12-26
I don't have an answer for you.  I know ldd will give you a list of dependencies for any installed binary, but I don't know how to do it for a deb.  I am watching this thread for an answer as well.

Art

---

### Post by artinla on 2007-12-28
bump

---

### Post by nick_h on 2007-12-30
Probably the best thing to do is run apt-get with the -s option.  This will simulate the install without actually doing it.
```
sudo apt-get -s install <package>
```
If you have a deb file and just want to see its dependencies then you can run:
```
dpkg -I <deb file>
```

---

### Post by erfahren on 2007-12-30
you can also do a --dry-run on a .deb using dpkg

"--no-act | --dry-run | --simulate
Do everything which is supposed to be done, but don't write any changes. This is used to see what
would happen with the specified action, without actually modifying anything."

dpkg man page: [http://www.debianadmin.com/manpages/dpkgmanpage.htm](http://www.debianadmin.com/manpages/dpkgmanpage.htm)

---

### Post by nick_h on 2007-12-30
> you can also do a --dry-run on a .deb using dpkg
Yes, this is the same as the -s option.

---

### Post by rbt123 on 2008-01-01
Thanks for the replies everyone! :)

---

