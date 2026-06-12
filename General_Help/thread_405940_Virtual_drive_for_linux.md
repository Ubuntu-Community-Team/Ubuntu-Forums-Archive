---
title: "Virtual drive for linux?"
date: 2007-04-10
forum: General Help
---

### Post by Aro on 2007-04-10
Does anyone know of a program for linux that is similar to [daemon tools?]("http://www.daemon-tools.cc/")

It's a virtual drive program that lets you mount iso and other cd/dvd images on virtual drives that act like actual cdroms.

---

### Post by thelinuxguy on 2007-04-10
> Does anyone know of a program for linux that is similar to [daemon tools?]("http://www.daemon-tools.cc/")


PowerISO has a free linux version but according to the website: "This is a free utility for linux which can extract, list, and convert image files (including ISO, BIN, DAA, and other formats)."
Doesn't mention mounting CDROM images though.

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)

> 
It's a virtual drive program that lets you mount iso and other cd/dvd images on virtual drives that act like actual cdroms.


For using the contents of an ISO, you can use
```

mkdir virtualcdrom
mount -o loop isofilename.iso virtualcdrom

```

Is this what you want?

---

### Post by solar george on 2007-04-10
If you are using the GUI you can extract the iso with file-roller Xarchiver or the like.

---

### Post by Oki on 2007-04-10
[http://linuxappfinder.com/package/kiso](http://linuxappfinder.com/package/kiso)

Type kiso in synaptic to install.

---

### Post by kpkeerthi on 2007-04-10
[CDEmu]("http://ubuntuforums.org/showthread.php?t=276743")

---

### Post by pilot550 on 2007-04-15
AcetoneISO is what you want.
[http://kde-apps.org/content/show.php?content=44805]("http://kde-apps.org/content/show.php?content=44805")

---

### Post by tlacuache on 2007-04-16
Check out one of these threads:

[http://ubuntuforums.org/showthread.php?t=276743](http://ubuntuforums.org/showthread.php?t=276743)

or 

[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

I prefer CDemu myself.

-SG

---

### Post by das letzte einhorn on 2008-03-21
I have tried to install CDEmu, and it tells me that I have the wrong architecture. is it only compatible with Ubuntu 32 bit? (I have U7.10)

---

### Post by bulletxt on 2008-03-22
the only GUI program actually working out of the box and that does what you need and a lot of other things is AcetoneISO2.
get it here:
[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

of course if you are on a 64bit OS download the source package and follow the README instructions.

---

