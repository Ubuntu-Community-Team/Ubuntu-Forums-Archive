---
title: "download .deb on the desktop"
date: 2007-02-20
forum: General Help
---

### Post by Dom93 on 2007-02-20
hi all,
i'm italian.
i want download to the desktop the packages that I have found in synaptic.
i dont found the packages to use "search"...:( 
how I can make?:confused: 

tnx

	
salutes from Italy :KS

---

### Post by taurus on 2007-02-20
You want to install the file that you just downloaded!  You can either double-click it or open a terminal and install it with

Applications -> Accessories -> Terminal
```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by JamieC on 2007-02-20
You could try copying the packages you've installed to the desktop, chances are most of them have been removed via cleaning operations though:
```

mkdir ~/Desktop/archives
cp /var/cache/apt/archives/*.deb ~/Desktop/archives

```

You will find a folder on your desktop containing all your archived packages.

To download packages without installing them, you can do the following (where <package> is the name of the package):
```

mkdir ~/Desktop/archives
cd ~/Desktop/archives
sudo aptitude download <package>

```

---

### Post by Dom93 on 2007-02-20
tnx 1k!!!
i have I have resolved with the method of JamieC

Byez

---

