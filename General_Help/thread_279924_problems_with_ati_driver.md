---
title: "problems with ati driver"
date: 2006-10-18
forum: General Help
---

### Post by gummygod on 2006-10-18
DISREGUARD THE FOLLOWING(i used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) method 2 and found out i lacked some installation tools, anyways driver is now working!):



i know theres alot of problems with this(installing an ati driver), but i know i installed it previously.  recently i realized i had the wrong kernal version, i had 386 when i should have had 686. so i installed the correct one for my P4 HT processor. after this i noticed my ati driver is no longer installed, mesa's there again.  so i tried to install the driver again but when i run the driver i dl from ati's site this comes up
```
Detected configuration:
Architecture: i686 (32-bit)
X Server: XFree86 4.6.0

Detected version of X does not have a matching 'x460' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install
```

does anyone know what i need to do to get past this? i tried "sudo X_VERSION=x430 ./ati-driver-installer-8.29.6.run --install" to no avail.  any help would be greatly appreciated.

---

### Post by pay on 2006-10-19
386 and 686 aren't the kernel version. They just mean they are more specialised for different processors. The part "2.6.18" is the kernel version.

---

