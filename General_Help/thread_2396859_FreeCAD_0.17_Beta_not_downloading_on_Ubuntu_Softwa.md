---
title: "FreeCAD 0.17 Beta not downloading on Ubuntu Software centre"
date: 2018-07-21
forum: General Help
---

### Post by flyinghigh2 on 2018-07-21
Hi 

As the title suggests really.

it gives this error;

""Detailed errors from the package manager follow:

snapd operation finished with error cannot perform the following tasks:
- Download snap "freecad" (4) from channel "stable" (invalid credentials)""

tried this with another CAD software sameish problem


anyone can help

thanks

robert

---

### Post by mIk3_08 on 2018-07-23
install inxi in your system;
type this command below in your terminal;
```
sudo apt-get install inxi
```
once installed; run this command in your terminal;
```
inxi -F
```
then copy and paste the result here in this thread

---

### Post by mIk3_08 on 2018-07-24
Install FreeCAD Ubuntu 18.04 Bionic
[(https://www.ubuntuupdates.org/package/core/bionic/universe/base/freecad)"]Click Here]("[https://www.ubuntuupdates.org/package/core/bionic/universe/base/freecad)
Install FreeCAD for Ubuntu Documentation
```
sudo apt install freecad freecad-doc
```
Freecad-doc U install the Documentation
Instead for the Latest one:
```
sudo apt install freecad-daily
```

---

### Post by mIk3_08 on 2018-07-24
[Click Here]("https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-stable") for ppa installation of FreeCAD.

---

