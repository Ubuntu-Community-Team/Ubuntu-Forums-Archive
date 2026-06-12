---
title: "Beep-media-player"
date: 2005-10-10
forum: General Help
---

### Post by SadaraX on 2005-10-10
Is there a way to get beep-media-player installed via apt-get without using the regular debian repositories? I can do it if I add the debian repo's to my apt source list, but to actually install the program apt would change a lot of my system including removing several programs like k3b.

---

### Post by 5-HT on 2005-10-10
Do you mean the debian repositories in place of ubuntu's repos?

Beep-media-player should be available in ubuntu's universe repo.

I don't have k3b installed myself, so I'm not sure if there are some conflicts occuring between the two, but if you were trying to use debians repos I'd suggest simply trying to install it from ubuntu's.

Hopefully there should not be any problems about needing to remove other progs in that case.

---

### Post by SadaraX on 2005-10-10
I am using Hoary, and I have this problem when I try to install bmp.

# apt-get install beep-media-player

The following packages have unmet dependencies:
  beep-media-player: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
                     Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
                     Depends: libvorbisfile3 (>= 1.1.0) but 1.0.1-1 is to be installed

I really only want to use the ubuntu repo's because it might cause complications for me if I use the debian ones along side them.

---

### Post by SadaraX on 2005-10-10
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

### Post by 5-HT on 2005-10-10
[QUOTE=SadaraX]I am using Hoary, and I have this problem when I try to install bmp.

# apt-get install beep-media-player

The following packages have unmet dependencies:
  beep-media-player: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
                     Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
                     Depends: libvorbisfile3 (>= 1.1.0) but 1.0.1-1 is to be installed

I really only want to use the ubuntu repo's because it might cause complications for me if I use the debian ones along side them.[/QUOTE]


It looks like with all the repos you're hitting, that apt's trying to install a newer version of beep-media-player (most likely from another repo) as the dependencies that you're seeing are higher than those needed by beep for me (version 0.9.7-1ubuntu1).



There are a few things you can try:

1. Let apt know which version you want: 

ex. sudo apt-get install beep-media-player=0.9.7-1ubuntu1

2. Trying to install it from the synaptic or aptitude GUI's which should let you see the correct version

3. Temporarily commenting out all the repos except those of ubuntu and see it that helps


I'd suggest trying #2 first as that should hopefully solve the problem right away.

Hope this helps.

---

