---
title: "git clone"
date: 2012-12-20
forum: General Help
---

### Post by ZombieApocalypse on 2012-12-20
Hi. Forgive my ignorance as I'm still a relative beginner in all things linux. :)

I want to update Playonlinux to the development version. On their website it states:

To get the latest developement version, open a terminal and type:
```
git clone https://github.com/PlayOnLinux/POL-POM-4
```

I did this and it did whatever it does (downloaded some stuff), but I still have the same version of POL (ie 4.1.8). What do I do next?

Thanks

---

### Post by Toz on 2012-12-20
The following works for me:

1. clone from git:
```
git clone https://github.com/PlayOnLinux/POL-POM-4
```

2. Enter the POL directory:
```
cd POL-POM-4
```

3. Change references of python/python2.6 to python2.7:
```
sed -i 's/python2.6 mainwindow.py/python2.7 mainwindow.py/g' ./playonlinux
sed -i 's/"$(which $PYTHON)"/"$(which python2.7)"/' ./playonlinux
sed -i 's/PythonBin="$PYTHON"/PythonBin="python2.7"/' ./playonlinux
```

4. Run POL
```
./playonlinux
```

Note You'll have to run POL from this directory to avoid interference with the package-installed version.

---

### Post by ZombieApocalypse on 2012-12-20
Brilliant, thanks.:D

---

