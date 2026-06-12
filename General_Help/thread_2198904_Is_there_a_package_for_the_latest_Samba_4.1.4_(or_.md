---
title: "Is there a package for the latest Samba 4.1.4 (or can I build one) for 12.04 LTS"
date: 2014-01-11
forum: General Help
---

### Post by starfry on 2014-01-11
Hi, I need to install Samba to a 12.04 LTS server for a project and "samba4-4.0.0~alpha18" doesn't cut it - I an official release version, like the latest 4.1.4 on offer at [http://www.samba.org](http://www.samba.org).

If there is a package containing this (or another recent-ish release version), where would I find it. I've searched with no luck!

Assuming I have to re-build the source, I have looked into how to rebuild a source package and have come up with something like this. First add source repos to `/etc/apt/sources.lst`
```

deb-src http://uk.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://uk.archive.ubuntu.com/ubuntu/ precise-updates universe

```
and, after updating (`apt-get update`) then doing this
```

sudo apt-get install build-essential fakeroot dpkg-dev devscripts
sudo apt-get build-dep samba4
apt-get source samba4
cd samba4-4.0.0~alpha18.dfsg1

```

What I don't know is where to go from here if I want to replace the package contents with upstream. I am used to ArchLinux where this kind of thing is transparent and easy. I'd appreciate someone who could explain how I should update the ubuntu package with the latest upstream ([http://samba.org/samba/ftp/stable/samba-4.1.4.tar.gz](http://samba.org/samba/ftp/stable/samba-4.1.4.tar.gz)) and rebuild it into a new updated package.

Thanks very much for your help.

---

### Post by mikewhatever on 2014-01-11
Samba 4 should be availabe in the next LTS, 14.04, so you can run the development release to enjoy it. I don't think 12.04 will ever have it.

---

### Post by Jason_Gibson on 2014-01-11
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html)

[http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)

Modifying the existing deb or changing the sources like you are talking about sounds overcomplicated to me. Just compile i from source directly from their svn then build a deb. I am by no means a compilation expert, have only done it twice. That being follow the first link to compile via the "Building The Binaries" section. Then package / install with the 2nd link. 2nd link is for Debian but Ubuntu is modified Debian unstable / testing so it should work fine. That should install, and create a .deb package for you. I've no real clue on sorting out dependencies though. I'm lazy about deps so after installing it I just **sudo apt-get -fy install** and call it a day.

---

### Post by starfry on 2014-01-13
Thank you for the replies. I had arrived at the same decision and was able to build 4.1.4 from sources. The reference to checkinstall was very helpful and I now have my own .deb for installing Samba. The only piece that I needed to add was an init script.

---

