---
title: "wxPython"
date: 2005-04-15
forum: General Help
---

### Post by PeteG on 2005-04-15
Hi,

I want to install Bittornado for my new ubuntu 5.04 box however i keep getting the message that i need libwxgtk2.4-python however when doing sudo apt-get install libwxgtk2.4-python i get the message that the package isn't available to be installed. This might be simple, but any help would be really appreciated! Thanks.

Pete.

P.S. When actually trying to find the version of python i had i accidentally typed python -v instead of python -V and i got a whole bunch of stuff come up. Anyone know what i did? lol.

---

### Post by Juergen on 2005-04-15
You probably haven't configured apt to use the universe etc. repositories.
Edit /etc/apt/sources.lst with sudo/as root and remove the '#' in front of the according lines.

To get an explanation of the various command line options of python just do
```
man python
```

---

