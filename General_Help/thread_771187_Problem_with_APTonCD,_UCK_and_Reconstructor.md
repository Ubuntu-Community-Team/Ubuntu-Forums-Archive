---
title: "Problem with APTonCD, UCK and Reconstructor"
date: 2008-04-27
forum: General Help
---

### Post by drbongo on 2008-04-27
I have upgraded to Hardy Heron and have been having problems with some apps! I usually download all the apps I want and then use APTonCD to copy the local package and install them on other machines. With Hardy APTonCD will make a CD iso of the packages but will not allow me to restore them to the apt cache! The CD is recognised by synaptic and will open up fine and allow me to install the packages, but I would rather copy them to the cache for later use, rather than carry a CD around with me.

The two remastering programs UCK and Reconstructor will not work with Hardy either. UCK cannot successfully create the becessary directories, and Reconstructor won't allow me to install anything using the terminal! This means I cannot remaster Hardy with my preferred apps included.

drbongo

---

### Post by rogerdean on 2008-05-31
there's a new version of remastersys out for hardy

[http://linuxmint.com/forum/viewforum.php?f=83](http://linuxmint.com/forum/viewforum.php?f=83)

see if this suits your needs...
cheers
Roger

---

### Post by zvacet on 2008-05-31
Maybe I´m wrong but I think all packages installed with synaptic or apt goes to the vat/cache/apt/archives.Install those packagesa with synaptic and see if they are in var/cache/apt/archives.If not you can allways make folder in your home directory and name it for example **folvar**.Copy packages from CD to that folder.After that go inside **folvar **folder and

```
cp * /var/cache/apt/archives
```

---

### Post by rogerdean on 2008-05-31
aptoncd is broken in hardy -  there's a fix coming. in the meantime you can install the unreleased fix from

[http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb](http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb)

---

### Post by Len_C on 2008-06-24
UCK is working with hardy. Read this bug report: [https://bugs.launchpad.net/uck/+bug/241797](https://bugs.launchpad.net/uck/+bug/241797)

(before using uck, you must install this package: 
[http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_i386.deb](http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_i386.deb) )

---

