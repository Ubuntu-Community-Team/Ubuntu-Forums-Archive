---
title: "[SOLVED] Installing package named the same as another package"
date: 2007-09-13
forum: General Help
---

### Post by x1a4 on 2007-09-13
Hi,

I want to install the Sun Download Manager.  I downloaded the RPM from Sun and converted it to DEB.  The name of the package is sdm.  The problem is that there already is a package in the repositories called sdm.  How do I modify the deb and change the name of the package?  Thank you.

---

### Post by Vadi on 2007-09-13
Right-click, Rename?

---

### Post by x1a4 on 2007-09-13
> **Vadi said:**
> Right-click, Rename?

Not the file name.  I need to edit the package name within the deb.

---

### Post by capink on 2007-09-13
```
mkdir -p ~/sdm/DEBIAN
```

```
dpkg --control /path/to/the/package.deb ~/sdm/DEBIAN
```

```
gedit ~/sdm/DEBIAN/control
```

This command will open the control file in a text editor (Replace Gedit with your favorite text editor). Replace the name in the Package field with a new name you want. Note the package name cannot contain spaces neither underscores.

```
dpkg --extract /path/to/the/package.deb ~/sdm
```

```
sudo chown -R root.root ~/sdm
```

```
dpkg -b ~/sdm ~/packagename.deb
```

Now you should have your new package in your home directory.

---

### Post by x1a4 on 2007-09-13
Thank you, it worked.

---

