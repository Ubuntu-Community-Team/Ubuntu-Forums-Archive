---
title: "Can't install djbdns (tinydns,dnscache)"
date: 2006-08-08
forum: General Help
---

### Post by Buckbeak on 2006-08-08
I'm trying to install Dan Berstein's dns software on Ubuntu Server 6.06. 

According to this, a source (installer) package is available, right?  : 
[http://packages.ubuntu.com/dapper/net/djbdns-installer](http://packages.ubuntu.com/dapper/net/djbdns-installer)

I've uncommented both the Universe and Multiverse sections of /etc/apt/sources.list and done a apt-get update. 

I can't seem to get the package with either apt-get install or apt-get source. It says unable to find a source package fpr djbdns-installer

I realize I could just download the tar file from Dan's website, but I prefer to use the package that Adam McKenna created.

---

### Post by Buckbeak on 2006-08-08
I fixed it myself. The standard lines in /etc/apt/sources.list, including the commented onces for multiverse were inappropriate. The multiverse lines refer to dapper-backports, they needed to be just dapper.

---

