---
title: "Problems with hplip-2.7.12 and HPPhotosmart C7200 and libsnmp9-dev"
date: 2008-01-19
forum: General Help
---

### Post by genekrupa on 2008-01-19
I tried to install the latest release of Hplip (2.7.12) under ubuntu 7.10 to be able to adress the scanner on our new HP Photosmart C7200

The installation stops when trying to resolve dependencies with apt-get install, saying

*Package install command failed with error code 100*

I went on and tried to install all the packages listed manually. 

It turns out there is one package missing in the repositories for Ubuntu 7.10, namely 
libsnmp9-dev. (Yes, I have made sure I have access to all repositories)

I googled it and came up with the information that 7.10 currently does not contain this package. 

Any idea how I get hold of this package?

Older versions of Ubuntu and Debian seem to contain it.

---

### Post by Buzzards on 2008-01-20
I just ran into exactly the same problem.

---

### Post by schierly on 2008-01-24
Just use this before you run the installer

```
sudo apt-get install libcupsys2 libcupsys2-dev build-essential python-dev python-dev python gs-esp libusb-dev xsane libsane python-reportlab python-qt3 libsnmp-dev openssl libjpeg62-dev libsane-dev libtool python-imaging
```

Hi guys,

I had the same problem.

The problem is that libsnmp9-dev is not available. The package  is called libsnmp-dev instead.

I installed it manually with the line above and it worked.

---

