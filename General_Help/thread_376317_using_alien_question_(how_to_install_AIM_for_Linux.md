---
title: "using alien question (how to install AIM for Linux)"
date: 2007-03-04
forum: General Help
---

### Post by DougieFresh4U on 2007-03-04
Very simple, how do I use alien once I have downloaded RPM ?? :confused:  Thanks

---

### Post by taurus on 2007-03-04
```
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```
Assuming you are in the directory where **filename.rpm** is located.

---

### Post by aysiu on 2007-03-04
Don't forget to install *alien* first: ```
sudo aptitude update
sudo aptitude install alien
``` You can also *alien install* it without taking the extra step to convert it to a .deb ```
sudo alien -i *filename.rpm*
```

---

### Post by DougieFresh4U on 2007-03-04
> **taurus said:**
> ```
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```
Assuming you are in the directory where **filename.rpm** is located.

 Hi taurus !! Not having any luck, of course I'm playing with AIM again-arghh:::dougie@DougiesToyBox:~$ alien aim-1.5.286-1.i386
Must run as root to convert to deb format (or you may use fakeroot).
dougie@DougiesToyBox:~$ sudo alien aim-1.5.286-1.i386
Password:
File "aim-1.5.286-1.i386" not found.
dougie@DougiesToyBox:~$ sudo alien aim-1.5.286-1.i386
File "aim-1.5.286-1.i386" not found.
dougie@DougiesToyBox:~$ sudo alien aim-1.5.286-1.i386.rpm
File "aim-1.5.286-1.i386.rpm" not found.
dougie@DougiesToyBox:~$

---

### Post by raul_ on 2007-03-04
make sure you're in the right path

---

### Post by taurus on 2007-03-04
If I remember it right, you somehow save everything to /tmp so you need to change to that directory first before you can run it.

```
cd /tmp
sudo alien aim-1.5.286-1.i386.rpm
sudo dpkg -i aim-1.5.286-1.i386.deb
```

---

### Post by aysiu on 2007-03-04
First of all, what's wrong with GAIM or Kopete?

And if you must install AIM, why not use the .deb file instead of the .rpm? ```
wget -c http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

---

### Post by DougieFresh4U on 2007-03-04
> **aysiu said:**
> First of all, what's wrong with GAIM or Kopete?

And if you must install AIM, why not use the .deb file instead of the .rpm? ```
wget -c http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

This is why I do not use the .deb::::dougie@DougiesToyBox:~$ wget -c [http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
--19:47:36--  [http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
           => `aim_1.5.286-2_i386.deb'
Resolving ftp.newaol.com... 205.188.105.50
Connecting to ftp.newaol.com|205.188.105.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,126,195 (1.1M) [text/plain]

100%[====================================>] 1,126,195    281.70K/s    ETA 00:00

19:47:41 (273.73 KB/s) - `aim_1.5.286-2_i386.deb' saved [1126195/1126195]

dougie@DougiesToyBox:~$ sudo dpkg -i aim_1.5.286-2_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-2_i386.deb
dougie@DougiesToyBox:~$:::::: and alien way tells me it cannot find file, thanks for help

---

### Post by taurus on 2007-03-04
Look at my previous post regarding /tmp.

---

### Post by fragos on 2007-03-04
Not all deb packages are equal.  One created for Debian might not work with Ubuntu.  Although I've had good luck the few times I conveted rpm to deb there are no gaurantees.  Before using an rpm make sure there isn't a comporable deb in the Ubuntu repositories.

---

### Post by aysiu on 2007-03-04
Repeating my earlier question: is there something wrong with GAIM or Kopete?

---

### Post by igknighted on 2007-03-04
AIM for linux is several years old and has almost no features.  If you are looking for anything like AIM in windows you will be very disappointed.

---

### Post by fragos on 2007-03-05
The Gaim installed from the Ubuntu repositories works fine for a number of protocols including AIM.  Not being a Windows user I have no idea if if the software AOL provides is more feature rich.  I can't imagine why anyone would want to install gaim from an rpm when a distro specific deb package is available.  For my taste I prefer gaim to kopete and haven't used kopete in a couple of years.

---

