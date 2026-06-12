---
title: "how to patch the source of a deb"
date: 2006-10-31
forum: General Help
---

### Post by cord on 2006-10-31
Hello all,
Unfortunately I am not very experienced in using the apt system so I was wondering how I would go about doing the following:

I want to basically rebuild the network manager package with a custom patch of sorts to test something. So I want to:
1. get the source code for the ubuntu "version" of network manager
2. patch it with my patch
3. make a deb file that I can install in place of the current network manager.

I am wondering how to build a deb from source and what (if anything) I need to do in order to set the proper compile flags etc... for the package to be compatible with my system.

Thanks in advance

---

### Post by 23meg on 2006-10-31
> **cord said:**
>  
I want to basically rebuild the network manager package with a custom patch of sorts to test something. So I want to:
1. get the source code for the ubuntu "version" of network manager```
sudo apt-get source network-manager 
```
> 2. patch it with my patchThe source files will be downloaded to the working directory. See [this]("http://http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html") for more information.
> 3. make a deb file that I can install in place of the current network manager.Execute ```
dpkg-buildpackage -rfakeroot -uc -b
```in the directory created.

---

### Post by matthewstory on 2006-10-31
in the sources.list file you need to uncomment the lines with src at the end . . . this is source, you can use apt to shag the source packages this way.  You can use aptitude (a CLI front end for the various apt apps) to search and install:

aptitude search network-manager

there should be a package there ending in src, insall it:

aptitude install <package name>

As far as building packages for ubuntu goes, you can use the dpkg suite to make your own packages.  Not too experienced with this, but a good how to can be found here:

[http://www.debian.org/doc/maint-guide/ch-build.en.html](http://www.debian.org/doc/maint-guide/ch-build.en.html)

---

### Post by cord on 2006-10-31
Thanks alot for the help.

I will try this early tomorrow and ask for more help if I need it.

<3 forums

---

