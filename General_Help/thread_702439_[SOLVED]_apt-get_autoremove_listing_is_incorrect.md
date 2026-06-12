---
title: "[SOLVED] apt-get autoremove listing is incorrect"
date: 2008-02-20
forum: General Help
---

### Post by eidauk on 2008-02-20
I installed Openoffice from the official debs by using dpkg. Now apt-get says:

```
The following packages were automatically installed and are no longer required:
  openoffice.org-writer openoffice.org-impress openoffice.org-draw
  openoffice.org-math openoffice.org-base openoffice.org-calc
The following packages will be REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-draw
  openoffice.org-impress openoffice.org-math openoffice.org-writer
0 upgraded, 0 newly installed, 6 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 219kB disk space will be freed.
```
Is there a way of excluding these from apt-get's autoremove list? If I run apt-get autoremove these apps will be removed. If I use autoremove in the future to clean up the system I'd be wiping out my Openoffice apps too!

Installing the openoffice in the repositories is not an option since it has too many bugs for what I use it for. That's why I used the official version.

---

### Post by kellemes on 2008-02-20
You can put those packages 'on hold' using one of the following methods...

[- Pinning]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin")
For example, I have in my /etc/apt/preferences the following packages 'on hold' like so..
```
Package: fglrx-kernel-src
Pin: version 8.43.2-2
Pin-Priority: 1001

Package: fglrx-driver
Pin: version 8.43.2-2
Pin-Priority: 1001

```[- wajig]("http://www.togaware.com/linux/survivor/Wajig_Overview.html")
So you have to..
```
apt-get install wajig
wajig hold <package_name>
```
[- aptitude]("http://nixdoc.net/man-pages/Linux/aptitude.1.html")
```
sudo aptitude
```Tjis gives you the pretty ncurses-gui from where you can use the menubar to hold packages.

- synaptic
```
gksudo synaptic
```From the menu's you can lock packages.

---

### Post by eidauk on 2008-03-04
I was able to lock those apps in Synaptic by clicking Packages > Lock Version. Thanks for the help.

---

