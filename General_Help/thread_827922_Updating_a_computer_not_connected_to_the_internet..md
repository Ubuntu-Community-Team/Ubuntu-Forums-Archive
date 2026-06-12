---
title: "Updating a computer not connected to the internet."
date: 2008-06-13
forum: General Help
---

### Post by Morichalion on 2008-06-13
Recently, I put together one of my old computers, put a clean install of ubuntu 8.04 on it, and gave it away. Unfortunately, I seem to have forgotten to put some minor essentials on the system, such as Wine and the codecs to play a DVD. 

A better solution than wine would be a simple application for making greeting cards that runs natively, since this is why she wants some windows compatibility. 

The new owner does not have internet access, and taking the computer back here to do the software updates is something I'd rather avoid, if possible. 

Basically, I need to know how to get the appropriate files in a *.deb package, on a cd, so i can get wine and dvd movie playing capabilities up and running on that machine.

---

### Post by kellemes on 2008-06-13
Never did this myself..
[http://planetoss.com/detail.php?id=13]("http://planetoss.com/detail.php?id=13")

Maybe others have better ideas.

---

### Post by editrix on 2008-06-14
There's a program called nonetdebs (I hope that's the name) that I've heard of but never tried.

Regarding the greeting cards, there's Scribus, which may have a greeting card template, or it would be easy enough to create one.

---

### Post by kalesh7 on 2008-06-14
usually you should be able to download .deb files from the respective programs sites or from getdeb.net or from repositories(I think). also you will need to get any dependencies that are not on the pc.
then you can install with 
sudo dpkg -i filename.deb
that should work(usually)

---

### Post by angry_johnnie on 2008-06-14
If you have another computer with the same version of Ubuntu, you could use aptitude to download any packages, and their dependencies.

For instance, libdvdcss would be something like:

```
sudo aptitude search libdvdcss
```

(because i think it's actually libdvdcss2 or some other number)

once you've found out what the actual name of the package is, you could

```
sudo aptitude show libdvdcss
```

(or libdvdcss2 or 3 or whatever)

**show** will display the package, a short description, and a list of dependencies.

Then you can use aptitude to download the package and its dependencies:

```
cd Desktop
```

(just because it's easier to see) :-)

then

```
sudo aptitude download libdvdcss some-package some-other-package
```

you can then take those packages to the other computer and install them with

```
sudo dpkg -i some-package.deb
```

---

