---
title: "Installing Wine In Ubuntu"
date: 2005-08-23
forum: General Help
---

### Post by sayyidhassan on 2005-08-23
I would like to install WINE on an Ubuntu desktop.i dont have internet connection on the Ubuntu machine,am using workplace internet which is running on WinXP.how do i download and install it on the UBUNTU machine.
Best regards
Hassan

---

### Post by raakken on 2005-08-23
don't know if I understand you right here, but you download it to a usb-storage of some kind or burn it to a cd...
then you enter the cd or the usb-device to your ubuntu, and install from there.
don't know if this helped you though
good luck

---

### Post by sigma2805 on 2005-08-23
try this

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by clehel on 2005-08-23
Once you have the binary deb package on your Linux machine, type the following in the console:

sudo dpkg --install <filename>

<filename> is the name with full path, unless you are in the directory where the deb package is.

---

### Post by Picklegnome on 2005-08-23
sigma2805- take a look at the link you gave. He said he doesn't have an internet connection, and that page gives instructions for using apt-get.

There are several threads on this topic- take a look at [http://ubuntuforums.org/showthread.php?p=312657](http://ubuntuforums.org/showthread.php?p=312657) for more detailed instructions. And if you have problems (like I did), it might help too.

Picklegnome

---

### Post by sayyidhassan on 2005-08-25
thanx.i will try that.am in a country where internet is still a priveledge and Windows is king.i want to change that

---

