---
title: "Skype not installing on 8.04, lib packages broken"
date: 2008-06-05
forum: General Help
---

### Post by sackbj on 2008-06-05
I an running 8.04 on a Lenovo X60 Tablet and I would like to install Skype.  Apt did not seem to have "skype" in it's repositories, so I downloaded the deb package from Skype.com.

I ran this command:
```
 sudo dpkg --install --force-architecture --force-depends skype-debian_2.0.0.68-1_i386.deb
```

as recommended by [*this*]("http://www.red91.com/articles/2008/05/11/install-skype-ubuntu-8-04") tutorial.  The terminal spat this out at me telling me that a couple of my packages were not installed.

```
Selecting previously deselected package skype.
(Reading database ... 129573 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.68-1_i386.deb) ...
dpkg: skype: dependency problems, but configuring anyway as you request:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
Setting up skype (2.0.0.68-1) ...

```

The output then says that Skype is broken and that libqt4-core would be reinstalled.  I reinstalled the two libqt4 libraries through the update manager, but Skype is still not installed.  How can I get Skype running?

---

### Post by Nepherte on 2008-06-05
It is probably a lot easier to install skyp using the medibuntu repositories: [http://www.medibuntu.org](http://www.medibuntu.org)
Enable their repository (see site), uninstall the skype you installed and install skype:
```
sudo apt-get install skype
```

---

### Post by sackbj on 2008-06-05
Thank you!  That worked perfectly!

---

