---
title: "broken install problem"
date: 2007-05-24
forum: General Help
---

### Post by rohan! on 2007-05-24
i was trying to install a .deb package for secondlife but lost my internet connection during its download* and quit the install (* the deb file is quite small and when you dpkg it it downloads the rest of the data) now every time that i attempt to run apt or any dpkg utilities i get the following message:

```
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
```

can't figure out how to fix it ... it won't even let me try and dpkg the deb again to fix the install. little stressed and tired with it now. any help would be great :(

---

### Post by gustavoberman on 2007-05-24
have you tried to uninstall the package first?
and then reinstall?

---

### Post by ryanVickers on 2007-05-24
Inside a folder called /var/cache/apt/archives is thousands of tiny package files (that actually add up to alot) but you fight find it in there.  Try removing it and see what happens

---

### Post by strabes on 2007-05-24
Try "sudo apt-get purge secondlife-install"

---

### Post by rohan! on 2007-05-26
> have you tried to uninstall the package first?
and then reinstall?
> Try "sudo apt-get purge secondlife-install"

it won't work; apt won't let me do anything, not even try and remove/reinstall the file :( i've even tried to use the deb package to install again, but that won't open

> Inside a folder called /var/cache/apt/archives is thousands of tiny package files (that actually add up to alot) but you fight find it in there. Try removing it and see what happens

i'll have a try at this as i've got nothing else to lose.

----
edit:
----
No it didn't work.

also I've noticed that a couple of other people have had the same problem [http://ubuntuforums.org/showthread.php?t=455111&highlight=secondlife](http://ubuntuforums.org/showthread.php?t=455111&highlight=secondlife) [http://ubuntuforums.org/showthread.php?t=454952&highlight=secondlife](http://ubuntuforums.org/showthread.php?t=454952&highlight=secondlife)

---

### Post by rohan! on 2007-05-26
i managed to reinstall secondlife from the deb file
```
sudo dpkg -i Desktop/secondlife-install_1.16.0.5-1~getdeb1_i386.deb
```
which has fixed the problem.

---

