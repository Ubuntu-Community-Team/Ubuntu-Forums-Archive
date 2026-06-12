---
title: "Installing Kompozer with add/remove"
date: 2007-11-19
forum: General Help
---

### Post by groping_blindly on 2007-11-19
Hi  all.

Here's a hitch I've been beating my head  against  with no luck whatsoever:

I'd like  to install Kompozer on my system, which I  understand  is a perfectly widespread common program which should be available via  the add/remove utility.   I've searched for it on friend's systems and sure enough it's there - but not on mine.  I've installed  all the available updates, I've enabled universe and multiverse repositories, I've checked every box I can find in every dialogue that looks even slightly relevant and when I run the search it's just not there.

The only thing I haven't done is a system wide upgrade to Gutsy.   Surely I should be able to get Kompozer for Fiesty? 

Any ideas?

---

### Post by Shazaam on 2007-11-19
Is this what you are looking for? If it is there is a .deb (Debian) file that you can download and install.

[http://kompozer.net/](http://kompozer.net/)

Also look in System>Administration>Synaptic Package Manager for it.

---

### Post by groping_blindly on 2007-11-19
Yeah,  that's the one.  I downloaded  the tar.gz but couldn't make it work - that's what started me  on the  forums in the first  place.  I've been assured  that I should be able to get Kompozer via  the  add/remove app.   and LOTS of users have advised me to avoid messing with manual installs.

I  tried  the .deb file and had more success than with anything else so far.  It downloaded  to the desktop and from there I was able to successfully install it on the system.  But now I can't find where it's installed, it's not on any of the application menus and I don't know where to find the program  or how to run it.

Argggggggggggggggggggggggh! . . . . . . .

---

### Post by Shazaam on 2007-11-19
Yes, .deb files are for Ubuntu. But with the proper tools you can install almost any type of package.

[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)



Open a terminal and type this in (configures any unconfigured packages)...
```
sudo dpkg --configure -a
```

And try a reboot, sometimes menu items don't show up until you do (there is a terminal command to refresh the menus but I forgot it sorry)

---

