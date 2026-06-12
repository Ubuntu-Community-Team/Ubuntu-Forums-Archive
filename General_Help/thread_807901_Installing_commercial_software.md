---
title: "Installing commercial software"
date: 2008-05-26
forum: General Help
---

### Post by qwes0c on 2008-05-26
Hi all! I am migrating to Linux, and I would like to install some commercial software I used to run on XP, such as Comsol Multiphysics. Problem is that there is no DEB package with it. 
I think I should install it as root. However, I don't want to screw up the directory structure, so I am asking: what is the most appropriate place for putting executables and license files? Something like /usr/local or /opt?
Thanks
Joe

---

### Post by teaker1s on 2008-05-26
does it have a linux .rpm file? if so it may work if you install with Alien

```
sudo apt-get install alien
```


In order to install one of the "foreign" packages (.RPM or .tgz), you'll first need to convert it do a .deb file, which is Debian's standard package format (and Ubuntu's as well). To do this, go into the terminal and change your directory to where your .RPM file is (we'll assume for this article that the .RPM file is on your desktop). That command is:

cd Desktop

Now that you're in the same "place" as the .RPM file, you'll want to convert it to a .deb file. You'll also want to make sure that the version number of the program stays as it should, so type the following (replace "program.rpm" with the actual name of the .RPM file you have):

sudo alien -k program.rpm

The "-k" in the above command tells alien to keep the version number, which would otherwise be changed to version "1" if not added.

---

### Post by shifty_powers on 2008-05-26
dude, if i were you, find another way than alien. just nto worth it. just answered a post about alien screwing someones apt up earlier today ;)

---

### Post by mlentink on 2008-05-26
Just checked their website, and they have a Linux (Debian) version available.
Do you have some kind of installation media?
Please keep in mind that you will *_not_* be able to install a windows version on your linux-box, it simply will not work. Most likely you will need to purchase a separate license for it, though you might be able to convince the maker to switch your license to the linux-version.

I do not know what this software does, but it might be worth your while to google around for FOSS-packages that perform similar functions.

---

### Post by qwes0c on 2008-05-27
Thanks all! Actually, the CD set allows for Win and Linux installation. Of course I know I cannot use the win executable to install on linux. There seems to be no RPM package set at all. Just a install.sh script that will trigger some java interface, which will then ask me what to do. Pretty much the same style as Windows. Of couse, as I wrote in my previous post, I can run the installation script either as root or as standard user, but I don't still know which one would be more appropriate....

---

### Post by teaker1s on 2008-05-28
your easiest way is copy the script from cd and change permissions so it can execute and try first without sudo and if it fails then with sudo

---

