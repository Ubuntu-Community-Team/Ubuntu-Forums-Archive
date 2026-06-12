---
title: "New User needs help installing Amarok"
date: 2008-03-16
forum: General Help
---

### Post by jc836 on 2008-03-16
I am converting from Windows XP SP-2 and Media Monkey library. The computer is a E Machines T1090 900mHz Celeron w/256megs of RAM.  Amarok appears to be parallel for me.  I downloaded the Amarok files and put them on a CD.  Then copied that to Ubuntu 7.10 and have a folder on the desktop.  I think the *.tar has been decompressed properly.  What do I do now?
Thanks to all who offer help.

---

### Post by p_quarles on 2008-03-16
Are you unable to connect the computer on which you want to install Amarok to the internet?

---

### Post by jc836 on 2008-03-16
The machine is currently stand alone and won't be web connected for some time.  Should I install Kubuntu to help with this?

---

### Post by p_quarles on 2008-03-16
Basically, compiling something as complex as Amarok from source code -- without an internet connection -- is going to give you a gigantic headache. 

The binary packages for Amarok are here:
[http://packages.ubuntu.com/gutsy/kde/amarok](http://packages.ubuntu.com/gutsy/kde/amarok)

Note that **all** of the packages with red dots next them are required before Amarok itself will be installed. You already have many of these packages, but not all of them. In order to get Amarok working with patent-encumbered codecs, you will also need the package kubuntu-restricted-extras, along with all of its dependencies. This would also be true if you installed using the Kubuntu CD, which does not include the restricted-extras package for legal reasons.

Basically, if there's any way to get this computer networked -- even temporarily -- it will be a breeze. If not, you are looking at a complex task.

If you decide to download all of the individual packages and transfer them via portable media, you can use the following command to install them (individually):
```
sudo dpkg -i *package_name*.deb
```
If the package has dependencies which are not yet installed, it will exit with an error, and tell you which ones are missing. This is known as "dependency hell," an old frustration that was largely solved by network-based package managers. Proceed at risk to your own sanity. ;)

---

### Post by jc836 on 2008-03-16
Thank you for your help. 
I will run a cable for the machine and come back when that is done.

---

### Post by jc836 on 2008-03-17
Update-I installed Kubuntu and Amarok 1.4.7 installed as part of the package. Now I need to work on cabling and installing several additional cards.  Are new cards automatically detected?  Also Kubuntu does not come with Firefox-can I download from Mozilla and directly install it?
Again thanks for the help in getting me started.

---

### Post by zvacet on 2008-03-17
KDE is bit different and I don´ use it but still I think it comes with Firefox.Search from desktop ans see if you can find** internet>web browsers**.If you don´t find Firefox use Konqueror.

---

### Post by p_quarles on 2008-03-17
Yes, you can install anything that's in the repositories on any version of Ubuntu. Just load up the package manager and search for what you want. 

Assuming that you mean network cards, there's an easy way to find out. Once you've plugged them in and rebooted, run this:
```
ifconfig -a
```
This will list all available network interfaces, along with their status and device names. Generally, the first interfaces will be known as eth0, with the next being eth1, and so forth.

---

