---
title: "Installing Iceweasel"
date: 2007-08-15
forum: General Help
---

### Post by lakelovers on 2007-08-15
I'd like to give Iceweasel a try but have been unable to install it even after following instructions on Ubuntu. I have iceweasel-1.5.0.7-ubuntu-i386.deb on the desktop and extracted into my home folder. I've tried "dpkg iceweasel/*  as root while in /home/iceweasel/ which gives me an error message. What am I not doing right?

---

### Post by merlinus on 2007-08-15
Did you try using GDebi Package Installer to install rather than extract it?

-merlin

---

### Post by kerry_s on 2007-08-16
just click on the .deb. there is no difference other than a change in icons and a new name, it is still firefox.

---

### Post by vexorian on 2007-08-16
> **lakelovers said:**
> I'd like to give Iceweasel a try but have been unable to install it even after following instructions on Ubuntu. I have iceweasel-1.5.0.7-ubuntu-i386.deb on the desktop and extracted into my home folder. I've tried "dpkg iceweasel/*  as root while in /home/iceweasel/ which gives me an error message. What am I not doing right?
why would you do it? afaik it is just a repackaged firefox that uses another name so mozilla doesn't get mad? or did the debian guys added features?

---

### Post by bettlebrox on 2007-08-16
dpkg -i iceweasel-1.5.0.7-ubuntu-i386.deb

will install it.

---

### Post by lakelovers on 2007-08-16
Merlin. . . I'm not familiar with GDebi package installer. Where do I find it?
Vexorian. . . Firefox crashes whenever I go to a secure login site.
Bettlebrox. . . dpkg -i iceweasel-1.5.0.7-ubuntu-i386.deb is what I've been trying and I get this: "error processing iceweasel-1.5.0.7-ubuntu-i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 iceweasel-1.5.0.7-ubuntu-i386.deb"

Does this mean I'm in the wrong folder? I've opened the directory and did "ls" in the terminal and iceweasel is listed. So that where I've used the command you suggested.
Jerry

---

### Post by vexorian on 2007-08-16
> Vexorian. . . Firefox crashes whenever I go to a secure login site. yes , but since iceweasel it is a repackaged firefox, that may not fix your issues.

to install a .deb you only need to double click it,

---

### Post by bettlebrox on 2007-08-16
> **lakelovers said:**
> Merlin. . . I'm not familiar with GDebi package installer. Where do I find it?
Vexorian. . . Firefox crashes whenever I go to a secure login site.
Bettlebrox. . . dpkg -i iceweasel-1.5.0.7-ubuntu-i386.deb is what I've been trying and I get this: "error processing iceweasel-1.5.0.7-ubuntu-i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 iceweasel-1.5.0.7-ubuntu-i386.deb"

Does this mean I'm in the wrong folder? I've opened the directory and did "ls" in the terminal and iceweasel is listed. So that where I've used the command you suggested.
Jerry

I'm not sure what your trying to do, but did you extract the .deb file? U don't have to do that, use the package manager to install it (using dpkg) or one of the GUI tools.

---

### Post by merlinus on 2007-08-16
GDebi package installer came with my ubuntu install.  I simply right-click on a deb file, and have the option to Open with GDebi Package Installer.

It will also download and install any needed dependencies.

-merlin

---

