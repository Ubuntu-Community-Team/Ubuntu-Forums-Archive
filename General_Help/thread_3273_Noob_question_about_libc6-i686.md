---
title: "Noob question about libc6-i686"
date: 2004-11-04
forum: General Help
---

### Post by andbert on 2004-11-04
I've tried to install Mplayer using Synaptic...
Some errors occur, and i think i has something to do with libc6-i686:

mplayer-586:
 Avhenger av: libartsc0 but it is not going to be installed
 Avhenger av: libggi2 but it is not going to be installed
  Avhenger av: libungif4g but 4.1.0b1-6 is to be installed

F.e. Synaptic says the Libc6-i686 package is damaged


dpkg -s libc6-i686 gives me:

Package: libc6-i686
Status: deinstall reinstreq half-installed
Priority: extra
Section: libs
Installed-Size: 2132
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.2.ds1-13ubuntu2
Config-Version: 2.3.2.ds1-13ubuntu2
Pre-Depends: libc6 (= 2.3.2.ds1-13ubuntu2)

Could anyone give me a hint here? Im totally new to Ubuntu (or Linux) but have no fear for the command line....

---

### Post by TekMate on 2004-11-04
Try typing apt-get -f install in a terminal and then trying again.

---

### Post by andbert on 2004-11-04
Argh

Some error messages saying that the package is in bad shape, inconsistant.
And that i should reinstall it before attempt to delete it.
Even though I've already tried that....


ab

---

