---
title: "Assemble a deb"
date: 2008-02-23
forum: General Help
---

### Post by th1bill on 2008-02-23
[http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb](http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb)

The page above is binary code for Wine Doors, can anyone tell me how to assemble it as it is written for Debian and Ubuntu and I'm hoping it will run Photo Plus from Serif Software.

---

### Post by rapiscan on 2008-02-23
This is is a debian package, and you would use dpkg to install it.

Right click on the link and click 'Save as' to save the file to your computer.  I believe Gutsy allows you to just double click on the package to install it.  

If that doesn't work, you can simply do it from command line.  Open your terminal and go to the directory that you saved the package in.  use ```
dpkg -i package.deb
``` to install the package. Depending on how the package installs you may need to use sudo, like this: ```
sudo dpkg -i package.deb
```
Of course, package.deb is the name of the actual package that you downloaded

---

