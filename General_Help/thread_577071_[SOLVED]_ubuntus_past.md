---
title: "[SOLVED] ubuntus past"
date: 2007-10-15
forum: General Help
---

### Post by linux noooob on 2007-10-15
well i would like to ask out of being a curious Linux user. how do they make the installation cd's? like say how do you take Debian add gnome and other programs and create a live  cd and installation cd from it?

---

### Post by ruibernardo on 2007-10-15
This reading might interest you to know more about it:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")
[Ubuntu Customization Guide - Quick Start]("http://ubuntuforums.org/showthread.php?t=186792")

There is a simpler (graphical) way to create you own version of Ubuntu, with [Reconstrutor]("http://reconstructor.aperantis.com/index.php").

---

### Post by linux noooob on 2007-10-15
hey do you think if i used Debian and made my own distro i could use reconstructor as a way to make an installation cd?

---

### Post by ruibernardo on 2007-10-15
I don't think so, as reconsrutor was made to be used with Ubuntu, but I've never tried with a Debian CD, although I don't think it would work.

I would suggest you to begin testing reconstructor and removing all the packages that you don't like (or don't want), and then add some packages you want. It is very easy with reconstructor. Look at their tutorial [here]("http://reconstructor.aperantis.com/cgi-bin/moin.cgi/Docs/Using_Reconstructor").

The real job of changing Debian unstable to Ubuntu is a little bit more complicated (not that little, it is a huge transformation really). This text [here]("http://people.debian.org/%7Eosamu/hackdi/ch-d-i.html"), for example, is to make a custom installer CD (not a LiveCD) of Debian. For a LiveCD (for Debian or Ubuntu) you must change casper and ubiquity packages (look at the first links I gave you on my previous post about LiveCD and InstallCD customization and search for those words).

---

### Post by linux noooob on 2007-10-15
i was looking more for an installer cd creator not  as much a live cd

---

### Post by ruibernardo on 2007-10-15
I've not tried to use reconstructor with the InstallCD, but apparently it [is  supported]("http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=630") (it wasn't when I've played with it). So, you can use reconstructor to remove and add the packages you want.

Also, to make this the right way (the hard way, but where you learn more) please check again [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization).

(sorry, I've posted the LiveCDCustomization twice on my first post)

I've search for some more info about the "transformation" from Debian to Ubuntu, but didn't found any really useful. Maybe somebody could post it here just for the record.

---

### Post by linux noooob on 2007-10-16
Thanks you have been alot of help! if you do find any more information i would be very thankful
odd it says SOLVED?

---

