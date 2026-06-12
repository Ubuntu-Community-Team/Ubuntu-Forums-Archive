---
title: "How to go up the dependency tree?"
date: 2017-03-11
forum: General Help
---

### Post by PaulBx on 2017-03-11
There appears to be a lot of information and a lot of ways to find the dependencies of a package. What I want to do is go in the other direction: given that I have a library installed, what packages list that library as a dependency? I haven't been able to find out how to do that.

---

### Post by vasa1 on 2017-03-11
Look at ```
apt-cache showpkg package_name
``````
apt-cache depends
```and```
apt-cache rdepends
```I'm sure there are some pretty tricks using dpkg as well.
Not confirmed but my notes tell me that```
dpkg-query -S /path/to/filename
```finds which package installed the file.
So,```
dpkg-query -S /sbin/apparmor_parser
```returns```
apparmor: /sbin/apparmor_parser
```

---

### Post by Impavidus on 2017-03-12
Synaptic can also tell you that: click on the package, click on properties.

Sometimes I mark a package for uninstall, which gives a list of all installed packages that depend on it and would be uninstalled too. Then, obviously, I cancel.

---

### Post by PaulBx on 2017-03-12
I tried "apt-cache depends stellarium" and got a list of dependencies including zliblg and stellarium-data. I then tried "apt-cache rdepends stellarium-data" which not surprisingly gave me stellarium as a result. I then tried "apt-cache rdepends zliblg" and it gave me nothing even though stellarium allegedly depends on it. Further investigation tells me zliblg is not on the system ("showpkg" told me). I guess having a dependency does not necessarily imply that dependency is installed.

Anyway thanks for these tips, they will help me figure out some things with my system.

---

### Post by vasa1 on 2017-03-12
> **PaulBx said:**
> I tried "apt-cache depends stellarium" and got a list of dependencies including zliblg and stellarium-data. I then tried "apt-cache rdepends stellarium-data" which not surprisingly gave me stellarium as a result. I then tried "apt-cache rdepends zliblg" and it gave me nothing even though stellarium allegedly depends on it. Further investigation tells me zliblg is not on the system ("showpkg" told me). I guess having a dependency does not necessarily imply that dependency is installed.

Anyway thanks for these tips, they will help me figure out some things with my system.

Isn't it [FONT=Courier New]zlib_1_g[/FONT]?

Stellarium's depends are:```
stellarium-data (= 0.14.3-1), libc6 (>= 2.15), libgcc1 (>= 1:3.0), libgl1-mesa-glx | libgl1, libqt5core5a (>= 5.5.0), libqt5gui5 (>= 5.2.0), libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0), libqt5network5 (>= 5.0.2), libqt5opengl5 (>= 5.0.2) | libqt5opengl5-gles (>= 5.0.2), libqt5script5 (>= 5.0.2), libqt5serialport5 (>= 5.1.0), libqt5widgets5 (>= 5.2.0), libstdc++6 (>= 5.2), zlib_1_g (>= 1:1.1.4)

```
And the reverse depends of zlib1g are too many to post.

---

