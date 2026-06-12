---
title: "wavpack"
date: 2005-10-10
forum: General Help
---

### Post by SadaraX on 2005-10-10
Is there anyway to get wavpack and wavunpack to install via regular apt-get? When I try to install them, I get:

# apt-get install wavpack
The following packages have unmet dependencies:
  wavpack: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
           Depends: libwavpack0 (>= 4.2.0) but it is not going to be installed
E: Broken packages

Here is my apt-source list

# ------------------------------------------------------------------------- 

# Ubuntu General -- Hoary
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

# Ubuntu Updates -- Hoary
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

# Ubuntu Universe/Multiverse -- Hoary
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse

# Ubuntu Official Backports -- Hoary
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

# ------------------------------------------------------------------------- 

# Ubuntu Security -- Main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# Ubuntu Security -- Universe/Multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

# ------------------------------------------------------------------------- 

# Nerim Repository - General - Source
#deb-src [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

# -------------------------------------------------------------------------

# Nerim Repository - i386 - Stable
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

# Nerim Repository - i386 - Testing
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

# Nerim Repository - i386 - Experimental
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) experimental main

# Nerim Repository - i386 - Unstable
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

# -------------------------------------------------------------------------

# RareWares Repository - Experimental
deb [http://www.rarewares.org/debian/packages/experimental/](http://www.rarewares.org/debian/packages/experimental/) ./

# RareWares Repository - Unstable
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

# -------------------------------------------------------------------------

# FBriere.net - Stable
deb [http://www.fbriere.net/debian/dists/stable](http://www.fbriere.net/debian/dists/stable) /

# FBriere.net - Testing
deb [http://www.fbriere.net/debian/dists/testing](http://www.fbriere.net/debian/dists/testing) /

# FBriere.net - Unstable
deb [http://www.fbriere.net/debian/dists/unstable](http://www.fbriere.net/debian/dists/unstable) /

# -------------------------------------------------------------------------

# Debian Linux - Primary Repository
#deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) testing main contrib non-free
#deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) unstable main contrib non-free

# -------------------------------------------------------------------------

---

### Post by xmixahlx on 2005-10-11
yes, download the source tarball and compile install yourself.

all of the rarewares source (and, old packages, if you want to try an older one) are at [http://xmixahlx.dyndns.org/debian/](http://xmixahlx.dyndns.org/debian/)


later

---

