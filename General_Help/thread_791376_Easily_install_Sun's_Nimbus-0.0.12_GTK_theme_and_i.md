---
title: "Easily install Sun's Nimbus-0.0.12 GTK theme and icons"
date: 2008-05-12
forum: General Help
---

### Post by diamondsw on 2008-05-12
[IMG]http://www.vinodlive.com/wp-content/uploads/2007/08/nimbus-theme.png[/IMG]

After taking a peek at OpenSolaris (great tech, nicely laid out, meager package repository), I wanted to bring its Nimbus theme to my Ubuntu install. Here are the fruits of this work. :)

I took the basic information [found here](http://www.vinodlive.com/2007/08/20/make-your-ubuntu-desktop-more-beautiful/) and updated it for the current version of Nimbus (0.0.12 as of this writing) and updated some of the package additions for the current Ubuntu (8.0.4).

A copy of the install script is on my server [here](http://diamondsw.dyndns.org/Misc/Ubuntu/Nimbus/build-nimbus-0.0.12.sh). It will download Nimbus from Sun, the patch file from my server (feel free to browse it - I didn't create any of it, just updated it), and optionally allow you to use the OpenSolaris logo to avoid the overly-large JDS logo on the main menu.

**NOTE:** This script must be run as root to install packages and such, so you must run it as sudo.

```
# wget http://diamondsw.dyndns.org/Misc/Nimbus/build-nimbus-0.0.12.sh
# chmod a+x build-nimbus-0.0.12.sh
# sudo ./build-nimbus-0.0.12.sh
```


Here it is, in case you'd like to take a look at what's involved:

```
#!/bin/bash

# ---------- Set a few script variables ----------
REMOVE_WORK=true
OPENSOLARIS_LOGO=false
WORK_DIR="work"

# ---------- Create a working directory ----------
BASEDIR=`pwd`
mkdir ${WORK_DIR}
cd ${BASEDIR}/${WORK_DIR}

# ---------- Install necessary packages ----------
apt-get -y install build-essential libgtk2.0-dev
apt-get -y install intltool icon-naming-utils fakeroot devscripts debhelper

# ---------- Download source packages ----------
wget -c http://dlc.sun.com/osol/jds/downloads/extras/nimbus-0.0.12.tar.bz2
wget -c http://diamondsw.dyndns.org/Misc/Nimbus/nimbus-0.0.12.diff.gz
tar -xf nimbus-0.0.12.tar.bz2

# ---------- Apply the patches ----------
if $OPENSOLARIS_LOGO; then
	cd ${BASEDIR}/${WORK_DIR}/nimbus-0.0.12/
	rm -f icons/*/places/start-here.png
	cd icons/24x24/places/
	wget -c http://diamondsw.dyndns.org/Misc/Nimbus/start-here.png
	cd ${BASEDIR}/${WORK_DIR}/nimbus-0.0.12/
	wget -c http://diamondsw.dyndns.org/Misc/Nimbus/opensolaris-logo.diff.gz
	zcat opensolaris-logo.diff.gz | patch -p1
	cd ${BASEDIR}
	wget -c http://diamondsw.dyndns.org/Misc/Nimbus/opensolaris-default.jpg
fi
cd ${BASEDIR}/${WORK_DIR}/nimbus-0.0.12/
zcat ../nimbus-0.0.12.diff.gz | patch -p1

# ---------- Create the *.deb packages ----------
chmod +x debian/rules
intltoolize --force
fakeroot dpkg-buildpackage -us -uc -d

# ---------- Clean up the work folder ----------
cd ${BASEDIR}/${WORK_DIR}
mv *.deb ../
cd ${BASEDIR}
if $REMOVE_WORK; then
	rm -rf ${BASEDIR}/${WORK_DIR}
fi
```

---

### Post by toobuntu on 2008-05-15
Thank you for this!  I was having trouble with the errors resulting from the instructions on [http://www.vinodlive.com/2007/08/20/make-your-ubuntu-desktop-more-beautiful/]("http://www.vinodlive.com/2007/08/20/make-your-ubuntu-desktop-more-beautiful/"), and was just setting about to make some mods so it will work on Hardy...and then I found your script.

Two suggestions:

1. using aptitude instead of apt-get for installing packages from the repos.
2. adding an option to replace the distributor logo (on the main menu, etc.) with the **Ubuntu** logo, which can be found here: /usr/share/icons/Human/scalable/places/start-here.svg or here: /usr/share/pixmaps/ubuntu-screensaver.svg.

---

### Post by kiran_aryan on 2008-05-24
@diamondsw,
 nice work but you removed the files from your server too soon :(

---

### Post by wersdaluv on 2008-06-12
[http://gnome-look.org/content/show.php/Nimbus+(+Debian+and+Ubuntu+packages+)?content=70212](http://gnome-look.org/content/show.php/Nimbus+(+Debian+and+Ubuntu+packages+)?content=70212)

:)

---

### Post by diamondsw on 2008-07-07
> **kiran_aryan said:**
> @diamondsw,
 nice work but you removed the files from your server too soon :(

Oops! Fixed the link above.

---

### Post by cavarl on 2008-07-11
Hi, I've executed the script it downloaded something. What else should I do now? Should I reboot to see the effect?

I tried to install opensolaris before but had some problems with my sound card. But I think its theme is great.

Thanks

Edit: I searched files named nimbus and installed them.
Thank you very much! That looks great!

---

### Post by Snoober on 2008-09-17
Sweet! Thanks for the script!

---

