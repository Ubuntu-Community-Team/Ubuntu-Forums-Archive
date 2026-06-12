---
title: "Problems installing Traceroute"
date: 2016-01-14
forum: General Help
---

### Post by Ayshea on 2016-01-14
I have been asked to install traceroute, I searched about the Internet and I the following commands:

sudo add-apt-repository "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) $(lsb_release -sc) partner"

I then used this command:  sudo apt-get install traceroute

This is what came up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another sourceE: Package 'traceroute' has no installation candidate

Any Ideas?

---

### Post by matt_symes on 2016-01-14
Hi

> **Ayshea said:**
> I have been asked to install traceroute, I searched about the Internet and I the following commands:

sudo add-apt-repository "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) $(lsb_release -sc) partner"


The above command is not required and is usually used for installing PPAs.  You need to remove it.

If you're not sure how to do this then post back.

Anyway, traceroute is in the universe repository.

```

matthew-xu-16-04:/home/matthew/raspberry-pi-2-images:1 % acsh ^traceroute$
Package: traceroute
Priority: optional
Section: universe/net
Installed-Size: 173
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Laszlo Boszormenyi (GCS) <gcs@debian.org>
Architecture: amd64
Version: 1:2.0.21-1
Depends: libc6 (>= 2.14)
Filename: pool/universe/t/traceroute/traceroute_2.0.21-1_amd64.deb
Size: 45488
MD5sum: f30973d7576d208ebb7d30d0afde2347
SHA1: ce38d5c8171aceeb3951be6674aedd53229cdc5b
SHA256: b50fa14f4aa335067ee4228eaf31910afb1ddaf759e696732f5c95b9592ecf93
Description-en: Traces the route taken by packets over an IPv4/IPv6 network
 The traceroute utility displays the route used by IP packets on their way to a
 specified network (or Internet) host. Traceroute displays the IP number and
 host name (if possible) of the machines along the route taken by the packets.
 Traceroute is used as a network debugging tool. If you're having network
 connectivity problems, traceroute will show you where the trouble is coming
 from along the route.
 .
 Install traceroute if you need a tool for diagnosing network connectivity
 problems.
Description-md5: 8a3a47eccb961a38576ee994d96f3d2c
Homepage: http://traceroute.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

matthew-xu-16-04:/home/matthew/raspberry-pi-2-images:1 %
```

Enable the universe repository and try to install traceroute again.

If this fixes the issue for you then please mark this thread as solved using the thread tools under post #1.

Kind regards

---

### Post by slickymaster on 2016-01-14
Like matt_symes stated, traceroute is in the universe repository. You have to make sure that it's enabled in your sources list, which I'm almost convinced that you haven't, [judging form this thread]("http://ubuntuforums.org/showthread.php?t=2309882").

Once you've enable it, just run```
sudo apt-get install traceroute
```You can then perform a traceroute from the terminal by running```
traceroute yourdomain.com
```

---

