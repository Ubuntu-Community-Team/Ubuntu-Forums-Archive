---
title: "Installing via deb files"
date: 2005-09-15
forum: General Help
---

### Post by AndyT on 2005-09-15
I really have no idea which forum this question should be in so I hope it doesn't offend anyone.

I have downloaded the Ubuntu CD and installed in on my desktop, unfortunately it doesn't have an internet connection and there doesn't seem to be any help on the steps to installing deb files and their dependencies. Although I know Ubuntu isn't meant to be used this way it is part of the linux learning process.

Here comes the questions :)
I know where to download the .deb files and I know what the dependencies are. I also know how to install the .deb files. What I like to know is there a easy way (or a guide on installing deb files) to find out what dependencies I already have installed or dependecies needs installing for a particular package.

---

### Post by parktownprawn on 2005-09-15
[QUOTE=AndyT]

Here comes the questions :)
I know where to download the .deb files and I know what the dependencies are. I also know how to install the .deb files. What I like to know is there a easy way (or a guide on installing deb files) to find out what dependencies I already have installed or dependecies needs installing for a particular package.[/QUOTE]

try ```
apt-cache depends package-name 
```

to find out what packages depend on a particular package try 

```
apt-cache rdepends package-name 
```

although potentially out of date (see warning on page) the unofficial [http://packages.ubuntu.com](http://packages.ubuntu.com) may be another good  source of info

---

### Post by DirtDawg on 2005-09-15
I'm not sure this will help, but try the manual entrance to the Ubuntu repositories here:
[http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)
My Linux box also has no net, but when you find a package through this site, it lists and links to all dependancies, recommended add-ons, etcetera. 
That's how I go about it, anyways.

---

