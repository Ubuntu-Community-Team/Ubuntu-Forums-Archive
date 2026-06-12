---
title: "Broken package?"
date: 2012-11-05
forum: General Help
---

### Post by s0ny123 on 2012-11-05
When I tried to install some updates from the manager I got an error, that I should try sudo apt-get -f install, but that's what I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  sp-auth libboost-program-options1.46.1 wesnoth-1.10-l
  libboost-iostreams1.46.1 wesnoth-1.10-data wesnoth-1.10-thot
  wesnoth-1.10-aoi wesnoth-1.10-did wesnoth-1.10-core wesnoth-1.10-trow
  wesnoth-1.10-utbs wesnoth-1.10-low wesnoth-1.10-sof wesnoth-1.10-dm
  wesnoth-1.10-ei wesnoth-1.10-dw wesnoth-1.10-ttb wesnoth-1.10-tsg
  wesnoth-1.10-nr lib32stdc++6 wesnoth-1.10-httt wesnoth-1.10-music
  libboost-regex1.46.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxcb-render0
The following packages will be upgraded:
  libxcb-render0
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 0 B/13.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libxcb-render0 (--configure):
 libxcb-render0:amd64 1.8.1-1 cannot be configured because libxcb-render0:i386 is in a different version (1.8.1-1ubuntu0.1)
dpkg: error processing libxcb-render0:i386 (--configure):
 libxcb-render0:i386 1.8.1-1ubuntu0.1 cannot be configured because libxcb-render0:amd64 is in a different version (1.8.1-1)
Errors were encountered while processing:
 libxcb-render0
 libxcb-render0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zvacet on 2012-11-06
```
sudo dpkg --configure -a
```

---

### Post by s0ny123 on 2012-11-08
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

I still get this:

```
[~]$ sudo dpkg --configure -a
dpkg: error processing libxcb-render0 (--configure):
 libxcb-render0:amd64 1.8.1-1 cannot be configured because libxcb-render0:i386 is in a different version (1.8.1-1ubuntu0.1)
dpkg: error processing libxcb-render0:i386 (--configure):
 libxcb-render0:i386 1.8.1-1ubuntu0.1 cannot be configured because libxcb-render0:amd64 is in a different version (1.8.1-1)
Errors were encountered while processing:
 libxcb-render0
 libxcb-render0:i386


```

---

