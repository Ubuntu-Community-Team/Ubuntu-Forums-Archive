---
title: "Virtual box dependency problems"
date: 2007-07-26
forum: General Help
---

### Post by drfox on 2007-07-26
I'm trying to install Virtual box on Feisty.
I've tried the Synaptic package, and I get an error message: 
virtualbox:
 Depends: libxalan110  but it is not installable
 Depends: libxerces27  but it is not installable
I've tried installing from the deb from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and I get the error that it depends on libxalan110.
I've added deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free to my sources.list

Any other suggestions?

Larry

---

### Post by dje on 2007-07-27
Have you tried to install virtualbox using [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29") thats how i installed it.

---

### Post by dando80 on 2007-07-27
Most dependency problems (assuming you have the correct repos enabled) can be muddled through by using the "apt-cache search" command to find the correct package names and "apt-cache madison" to see what versions are available. Start out trying to install libxerces and libxalan and work your way backwards with any dependencies they have problems with. You should be able to find the conflict or what's missing.

---

