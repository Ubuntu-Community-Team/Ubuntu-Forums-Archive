---
title: "Having problems making Debian Packages- Please Help"
date: 2007-11-16
forum: General Help
---

### Post by Espreon on 2007-11-16
OK I am making a package for Prism and when I run the command that makes the package this is what the terminal gives me:

```

spanek@spanek-laptop:~$ dpkg -b /home/spanek/Desktop/prism prism_0.8.deb
dpkg-deb: can't mmap package info file `/home/spanek/Desktop/prism/DEBIAN/control': No such device

```

Heres the Info file:

```

Package: prism
Version: 0.8
Section: web 
Priority: optional
Architecture: i386
Depends: 
Essential: no
Installed-Size: 2480
Maintainer: Espreon
Provides: prism
Description: This app allows you to run web apps as desktop apps.

```

Thanks

---

### Post by rsambuca on 2007-11-16
Just double-click it and let gdebi install it for you.

---

### Post by Espreon on 2007-11-16
Huh? What does GDebi have to do with making Debian Packages?
I am making a .deb not trying to installing one.

---

### Post by rsambuca on 2007-11-16
Sorry,  I wasn't reading carefully.  My mistake.

---

### Post by Espreon on 2007-11-16
OK thats fine, we all make mistakes.

---

### Post by zvacet on 2007-11-16
> control 
The control file contains meta information about the package. Most of the fields in the file should be self-explanatory, so change any entries as necessary and put in short and long descriptions for the package. Note that any blank lines in the long description need to contain a single period. 
rules 
The rules file is a makefile that is executed at package build time to compile the package source into a binary. The file will have been automatically configured by dh_make to suit a typical build process, but if your package requires any unusual steps to be performed, you may need to edit the appropriate section of the rules file. 

It seams that is something wrong in control file.

---

