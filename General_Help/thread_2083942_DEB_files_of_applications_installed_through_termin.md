---
title: "DEB files of applications installed through terminal"
date: 2012-11-14
forum: General Help
---

### Post by balasankarc on 2012-11-14
Hi all,
I usually install applications via terminal. Where are the package files (.deb) stored for such apps??? If i backup them, it will save me from downloading again... so is there any way i can get those package files of apps i installed???

---

### Post by pkadeel on 2012-11-14
these are stored in /var/cache/apt/archive

you can setup a trivial repository for your downloaded packages using *dpkg*-scanpackages but you will need to install it first

please read
[http://www.debian.org/doc/manuals/repository-howto/repository-howto#id3032359](http://www.debian.org/doc/manuals/repository-howto/repository-howto#id3032359)
[http://www.debian.org/doc/manuals/repository-howto/repository-howto#using-a-repository](http://www.debian.org/doc/manuals/repository-howto/repository-howto#using-a-repository)

for more details

---

### Post by mcduck on 2012-11-14
it depends on *how* you installed them through terminal... ;)

If you are using apt-get (or Ubuntu Software Center or Synaptic), you'll find downloaded packages in /var/cache/apt/archives.

The package manager will automatically use existing packages instead of downloading again, but keep in mind that this only applies if the existing package is same or later version than the one in repositories. So if there's an updated package available, it will always be downloaded instead of using the cached version.

Also, running "sudo apt-get clean" will empty the cache. (or "sudo apt-get autoclean" to only remove old versions and packages that aren't installed at the moment)

---

