---
title: "sources.list"
date: 2005-09-30
forum: General Help
---

### Post by artinla on 2005-09-30
Could someone please post a current working sources.list with backports, universe, multiverse, etc?

Many of the sources are outdated in mine, and I get conflicting information searching the forum.

Thanks,

Art

---

### Post by matthew on 2005-09-30
Here is mine for Hoary. Everything is up to date as of today.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports and extras
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by artinla on 2005-09-30
Thanks

---

### Post by dhjohnson on 2005-10-01
I have the exact same sources.list, but I still can't install w32codecs.  I've also tried some debian .deb files--none of which are 100% compatible with ubuntu.  Any ideas?

---

### Post by Krag on 2005-10-01
Ditto.

I've got the same source file and I'm also missing w32codecs.

Search the forum but can't find any recent instructions, ubuntuguide.org seems to be out of date since backports were moved.

---

### Post by LinuxConvert on 2005-10-01
Hi guys

I kinda messed up my sources.list too and so I copied this one, but still all sorts of errors appear whenever I start Synaptic and when i refresh the package list... It looks like this:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)

Any suggestions?

LC

---

### Post by matthew on 2005-10-01
The wiki has been updated. Try the method outlined on this page for installing w32codecs.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

