---
title: "Oasis"
date: 2013-06-27
forum: General Help
---

### Post by OldManRiver on 2013-06-27
All,

Wanting to install OASIS from:

[http://oasis.sourceforge.net/](http://oasis.sourceforge.net/)

onto Ubuntu, so need to mod the install.php including code to find "Ubuntu", "Debian" and dependent libs, so can "wget" the right libs to get this installed.

If you have tried this an have some notes to share or are attempting this, would love sharing with you!

Cheers!

OMR

---

### Post by compiledkernel on 2013-06-27
That appears to be just a simple series of PHP scripts. If not much more than a CMS. I strongly suspect their arent any "per se" libs required for the install. 

Just download the tarball, unpack it into your Apache (or whatever webserver you use) www-root, and point your browser at the install.php instance. 

Unless Im missing something.

---

### Post by zQ6ML3J on 2013-07-30
> **compiledkernel said:**
> That appears to be just a simple series of PHP scripts. If not much more than a CMS. I strongly suspect their arent any "per se" libs required for the install. 

Just download the tarball, unpack it into your Apache (or whatever webserver you use) www-root, and point your browser at the install.php instance. 

Unless Im missing something.
C,

You are, the install code is full of bugs, been workng them off.  Actually have the installer working, but some of the libs shared with the installer, still error when trying to execute after install is complete.

Cheers!

OMR

---

### Post by zQ6ML3J on 2013-08-02
All,

Thread at: [http://ubuntuforums.org/showthread.php?t=2159450](http://ubuntuforums.org/showthread.php?t=2159450) is covering this in more detail, so will close this one, when user admins get my userID restored.

OMR

---

