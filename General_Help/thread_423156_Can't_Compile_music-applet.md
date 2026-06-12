---
title: "Can't Compile music-applet"
date: 2007-04-25
forum: General Help
---

### Post by lagartoflojo on 2007-04-25
I want to compile the latest music-applet (2.1.0) in Ubuntu Feisty. I downloaded the tar.gz file, extracted.
Then I did
```
$ sudo apt-get build-dep music-applet
$ sudo aptitude install python2.5-dev
$ sudo aptitude install python-gtk2-dev
$ sudo aptitude install python-gnome2-dev
$ ./configure --prefix=/usr **(no errors here)**
$ make **(no errors here, either)**

```

Then, I build the deb package with checkinstall:
```
$ sudo checkinstall
```
which goes fine until it tries to install the package:
```
Copying files to the temporary directory...OK
Striping ELF binaries and libraries...OK
Compressing man pages...OK
Building file list...OK
Building Debian package...OK
Installing Debian package... FAILED!
```
It asks me if I want to see the log, and it says the following:
```
(Reading database ... 105155 files and directories currently installed.)
Unpacking music-applet (from .../music-applet_2.1.0-1_i386.deb) ...
dpkg: music-applet: warning - conffile `etc/gconf' is not a plain file or symlin
k (= `/etc/gconf')
dpkg: music-applet: warning - conffile `etc/gconf/gconf.xml.defaults' is not a p
lain file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/hernan/Downloads/music-applet-2.1.0/music-applet_2.
1.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/hernan/Downloads/music-applet-2.1.0/music-applet_2.1.0-1_i386.deb
```

Anyone know what could be the problem?

---

### Post by taurus on 2007-04-25
Try

```
sudo checkinstall
```

---

### Post by lagartoflojo on 2007-04-25
> **taurus said:**
> Try

```
sudo checkinstall
```

Thanks... Actually I get that error running checkinstall with sudo... I just forgot to put it in my post. I changed the post accordingly.

---

### Post by lagartoflojo on 2007-04-25
bump.... no ideas?

---

### Post by CarpKing on 2007-05-22
I seem to be having this same problem: [http://ubuntuforums.org/showthread.php?t=421174&highlight=music-applet](http://ubuntuforums.org/showthread.php?t=421174&highlight=music-applet).  Has anyone compiled it successfully?

---

