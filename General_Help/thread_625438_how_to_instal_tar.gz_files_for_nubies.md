---
title: "how to instal tar.gz files for nubies"
date: 2007-11-28
forum: General Help
---

### Post by ameba on 2007-11-28
H

---

### Post by meatpan on 2007-11-28
The answer depends on what is inside the tar.gz file.  If you simply want to unpack the contents of the tar.gz (tarball) file, run ```
tar xzvf <file.tar.gz>
```, in the directory where you want the files.  The option string passed to tar means:
x:  'extract' the files
z:  the tarball is gzip compressed (usually indicated by the 'gz' suffiz)
v: print verbose output
f: extract from the supplied file (in the arg list)

Does this help?  If you need some more info, reply with a few details regarding what you want to do with the contents of the tarball.

---

### Post by ameba on 2007-11-28
wel

---

### Post by ameba on 2007-11-28
this

---

### Post by meatpan on 2007-11-28
Ok, it looks like you are downloading and installing a binary package.  The process you listed in the last post should 'install' the program.

Just curious, is there a reason why you don't want to install the ubuntu package?  Is is a versioning or permissions issue?   If not, consider installing the package using apt, via ```
sudo apt-get install clamtk
```

Installing using apt has tremendous benefits, such as automatic managment of dependencies and upgrades.

---

### Post by ameba on 2007-11-28
well

---

### Post by ameba on 2007-11-28
So

---

### Post by aysiu on 2007-11-28
> **ameba said:**
> well, i the version availible is obsolete from what i've read in the memo.
I don't know what memo you read, but the latest stable version of Clam AV is 0.91.2, according to [the Clam AV website](http://www.clamav.net/), and the latest version of Clam AV [in the Ubuntu repositories](http://packages.ubuntu.com/gutsy/utils/clamav) is also 0.91.2.

So, no, it's not obsolete.

**Step 1**
[Enable extra repositories](http://www.psychocats.net/ubuntu/source)

**Step 2**
Go to System > Administration > Synaptic Package Manager, search for *clamav*, right-click to mark the appropriate packages for installation, then click Apply.

---

