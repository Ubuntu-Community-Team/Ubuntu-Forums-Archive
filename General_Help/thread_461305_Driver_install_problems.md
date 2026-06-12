---
title: "Driver install problems"
date: 2007-06-01
forum: General Help
---

### Post by arden13 on 2007-06-01
I have installed both kubuntu and xubuntu on my computer (different partitions) and I need help.  I'm trying to install a D-link DFE-530TX+ PCI ehternet adapter, and it comes with the driver.  The problem is, I don't know what to do after I Un-Tar it.  In the .txt file it says to "compile it" but I don't know how to do that.  It comes with a Makefile, but I'm not sure what to do with it.  HELP!!!

---

### Post by arden13 on 2007-06-01
anyone?

---

### Post by bmartin on 2007-06-01
Normally, in the directory with the Makefile, there's a file called INSTALL or README that contains instructions. In a terminal, change to the directory that contains the Makefile, then perform the following commands:
```
sudo apt-get update
sudo apt-get build-essential
./configure
make
sudo make install
```
That should compile the program on your computer and install the necessary files. If the instruction are different in the INSTALL or README file, do what they say. The three last commands (./configure, make, make install) are the standard compile/install steps, but individual programs compile differently.

---

### Post by bmartin on 2007-06-01
This is a wired LAN adapter you're installing, right? I'm somewhat surprised it wasn't automatically detected and configured for use.

---

### Post by arden13 on 2007-06-01
yes its wired lan, but do those commands require an internet connection?  because we tried the commands and it recognized them, but it got an error...

---

### Post by arden13 on 2007-06-01
*bump*

---

### Post by bmartin on 2007-06-01
What was the error?

The commands that start with **sudo apt-get** require an internet connection. The other ones don't. Try using the last three commands only (starting with ./configure). If you get an error, please post it.

---

