---
title: "Error trying to install any new package with apt-get"
date: 2014-04-22
forum: General Help
---

### Post by eddie.moser on 2014-04-22
Hello All,

/boot filled up and near as i can tell caused a kernal update to have issues. I removed old kernal files with dpkg --purge and /boot now has space. but when i run apt-get -f install i get the following errors: 

```
dpkg: dependency problems prevent configuration of linux-server: linux-server depends on linux-image-server (= 3.2.0.56.66); however:
  Version of linux-image-server on system is 3.2.0.60.71.
 linux-server depends on linux-headers-server (= 3.2.0.56.66); however:
  Version of linux-headers-server on system is 3.2.0.60.71.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured

```

It has been a long time since I was running a server full time so any help is appreciated

---

### Post by TheFu on 2014-04-22
Try aptitude. It has been preferred by the Debian team for 5+ yrs. It is smarter about dependencies than apt-get, but uses most of the same options.

---

### Post by Jordan_Cameron on 2014-04-22
To me it seems Linux-server depends on an older version of linux-image-server than the one you have already... best bet if aptitude doesn't work is to rollback the packages somehow.

---

### Post by Impavidus on 2014-04-22
Rollback? Hmm, I'd say try and get linux-server version 3.2.0.60.71 installed. That's the latest version in the repos and the version depending on the installed versions of linux-image-server and linux-headers-server. If apt-get or aptitude doesn't believe linux-server 3.2.0.60.71 is available, try refreshing its memory with **sudo apt-get update** (or aptitude, if you prefer).

Anyway, linux-server is just a metapackage. You can always remove it, fix the problem and reinstall it.

---

