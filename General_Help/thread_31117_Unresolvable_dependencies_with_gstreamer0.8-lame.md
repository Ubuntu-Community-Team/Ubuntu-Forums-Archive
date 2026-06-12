---
title: "Unresolvable dependencies with gstreamer0.8-lame"
date: 2005-05-01
forum: General Help
---

### Post by cannibalbob on 2005-05-01
When I try to install gstreamer0.8-lame for mp3 support in sound juicer, I get:
> 
gstreamer0.8-lame:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

My sources.list is:

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main


does this mean I have to install it manually or find a repository that has it?

---

### Post by XDevHald on 2005-05-01
[QUOTE=cannibalbob]When I try to install gstreamer0.8-lame for mp3 support in sound juicer, I get:


My sources.list is:



does this mean I have to install it manually or find a repository that has it?[/QUOTE]
 It's asking for you to install  **libc6 **in which you might want to see if this package is installed, but is not being detected by synaptic, if so, reinstall it and try the same procedure again :)

---

### Post by cannibalbob on 2005-05-01
libc6 2.3.2.ds1-20ubuntu13 is installed.  synaptic thinks that's the latest version.

---

### Post by XDevHald on 2005-05-01
[QUOTE=cannibalbob]libc6 2.3.2.ds1-20ubuntu13 is installed.  synaptic thinks that's the latest version.[/QUOTE]
 Check the UbuntuForums backports, this may have already been requested.


[http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)

---

### Post by cannibalbob on 2005-05-02
is there a way to install an older version of gstreamer0.8-lame?

---

### Post by cannibalbob on 2005-05-02
so why does gstreamer0.8-lame depend on a package that isnt in the repository?

---

### Post by jdw on 2005-05-03
There's a slightly older version of gstreamer0.8-lame.deb on marillat that works, but you have to download it manually.  No biggie, just go here:

[ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/)

grab this one: gstreamer0.8-lame_0.8.8-0.1_i386.deb

(as opposed to the 0.8.8-0.2 one that Synaptic and apt-get wants us to use).

Then, just install it with dpkg like so:

sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb

Then just follow the directions on the [RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) page.

Someone should be told about this, but I'm pretty new to this community (former Gentooer!) so I don't know whom to inform.

---

