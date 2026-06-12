---
title: "Need help compiling 3d Mahjong please"
date: 2008-01-17
forum: General Help
---

### Post by kvonb on 2008-01-17
-

---

### Post by RebounD11 on 2008-01-17
Ok.. this worked for me:

first install alien:

```
sudo apt-get install alien
```

then download the Suse RPM of the game from here 
[http://www.reto-schoelly.de/mahjongg3d/mahjongg3d-0.96-SuSE_91.i586.rpm](http://www.reto-schoelly.de/mahjongg3d/mahjongg3d-0.96-SuSE_91.i586.rpm)

then do:

```
sudo alien -c -d <path-to-downloaded-RPM-package>/mahjongg3d-0.96-SuSE_91.i586.rpm
```

and it will create a DEB package in the same directory with the RPM package.

then simply install that DEB:

```
sudo dpkg -i <path-to-created-DEB-package>/mahjongg3d_0.96-1_i386.deb
```

You can now play the game by running:

```
mahjongg3d
```

in your terminal.

Hope this helps. Enjoy! :D

---

### Post by kvonb on 2008-01-17
-

---

### Post by RebounD11 on 2008-01-17
You're welcome :D

---

