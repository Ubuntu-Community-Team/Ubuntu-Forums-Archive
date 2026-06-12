---
title: "install kdevelop"
date: 2005-07-07
forum: General Help
---

### Post by pike on 2005-07-07
I have just installed Ubuntu 5.04 hoary and over it kunbuntu-desktop.

Now I'm trying to install kdevelop, but when i do that with synaptic it produces an error, it can't install automake and autoconf.

I don't find that packages with synaptic, Do I have to chage my sources.list?

I have already uncomment universe and multiverse lines in sources.list

How can I install kdevelop?

---

### Post by SGC on 2005-07-07
The version that in the universe repository of kdevelop is 2.1.5, try the latest version (3.2.1) from kubuntu repository:

Add the following line to sources.list:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then from the terminal:
sudo apt-get update
sudo apt-get install kdevelop

Or in synaptic: "reload" then "search" for kdevelop

If for some reason you want to stick with the old version in the universe repositoy, then please post the contents of your sources.list

---

### Post by pike on 2005-07-08
This is my actual apt sources.list:

```

# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://es.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://es.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Is correct?

---

### Post by pike on 2005-07-08
I have added the source you said me :

```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

and it said again that it can't install autoconf and automake

---

### Post by SGC on 2005-07-08
Your are missing two lines for the universe, add this:
```

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

```

---

### Post by SGC on 2005-07-08
[QUOTE=pike]I have added the source you said me :

```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

and it said again that it can't install autoconf and automake[/QUOTE]
 Could you post the exact message about the autoconf and automake

---

### Post by pike on 2005-07-13
I had comment sources.list line:

deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary main restricted

I uncommented it and now it work.

Thanks.

---

