---
title: "need help to run apple shake on ubuntu"
date: 2012-12-29
forum: General Help
---

### Post by howhy on 2012-12-29
i made a directory nreal inside usr directory and applied 755 permission to all the folder and files inside it, and even set the path to run apple shake
```
PATH=$PATH:/usr/nreal/shake-v4.10.0606/bin
```
I have also installed tsch since apple shake uses csh...
but now when I try to run shake i get error saying 
*/usr/nreal/shake-v4.10.0606/bin/shkx.exe: Command not found.*

where as all the stuff is their in the folder
howhy@UbuntuDesk:/usr/nreal/shake-v4.10.0606/bin$ lss
total 304
-rwxr-xr-x 1 root root  12478 Dec 29 20:17 mkpak
-rwxr-xr-x 1 root root   1028 Dec 29 20:17 shake
-rwxr-xr-x 1 root root  84940 Dec 29 20:17 shkv.exe
-rwxr-xr-x 1 root root 157328 Dec 29 20:17 shkx.exe
-rwxr-xr-x 1 root root   1030 Dec 29 20:17 tshake
-rwxr-xr-x 1 root root  29604 Dec 29 20:17 tshkx.exe

---

### Post by dino99 on 2012-12-29
this might help:

[http://forums.cgsociety.org/archive/index.php/t-806216.html](http://forums.cgsociety.org/archive/index.php/t-806216.html)

---

### Post by howhy on 2012-12-29
i just installed sudo apt-get install ia32-libs

since I am on 64 bit mahine and i downloaded 32bit libs but i do not know its location where it got installed .. how to get the location of those libs i just downloaded to

---

### Post by oldos2er on 2012-12-29
For newer versions of Ubuntu the package you need is named **ia32-libs-multiarch**.

```
dpkg -L <package name>
``` shows each file in a package and where it is installed.

---

### Post by howhy on 2012-12-29
> **oldos2er said:**
> For newer versions of Ubuntu the package you need is named **ia32-libs-multiarch**.

```
dpkg -L <package name>
``` shows each file in a package and where it is installed.

well, yesterday i did tried apt-cache search ia32-libs and found ia32-libs-multiarch in the list, 

however when i tried *dpkg -L ia32-libs-multiarch* i get message saying 
[I]Package `ia32-libs-multiarch' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.[/I]

so i tried sudo apt-get install ia32-libs-multiarch
then i got this 
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs-multiarch:i386 is already the newest version.
ia32-libs-multiarch:i386 set to manually installed.
The following packages were automatically installed and are no longer required:
  liblua5.1-lpeg2 liblua5.1-leg0 liblua5.1-filesystem0 lua5.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

so maybe I am doing something wrong being a newbie can u tell..?

---

### Post by oldos2er on 2012-12-30
Which version of Ubuntu are you using?

---

