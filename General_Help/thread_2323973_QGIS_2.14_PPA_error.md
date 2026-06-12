---
title: "QGIS 2.14 PPA error"
date: 2016-05-09
forum: General Help
---

### Post by luckystar3 on 2016-05-09
Hello all,
trying to install the latest version of QGIS and was trying to add it to the ppa when I got this error.

Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Translation-en
Fetched 3,344 B in 6s (527 B/s)                                                
Reading package lists... Done
W: GPG error: [http://qgis.org](http://qgis.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF5FFCAD71472C4

Can anyone lend a hand?

Additionally when I run sudo apt-get install qgis i get:

The following packages have unmet dependencies:
 qgis : Depends: libgdal1-1.7.0 but it is not installable
        Depends: libgeos-c1 (>= 3.2.2) but it is not installable
        Depends: libproj0 but it is not installable
        Depends: libqgis-analysis2.9.0 but it is not going to be installed
        Depends: libqgis-core2.9.0 but it is not going to be installed
        Depends: libqgis-gui2.9.0 but it is not going to be installed
        Depends: libqgis-networkanalysis2.9.0 but it is not going to be installed
        Depends: libqscintilla2-8 but it is not installable
        Depends: libspatialite3 (>= 2.4.0~rc2) but it is not installable
        Depends: qgis-providers (= 1:2.9.0+git20150525+cec5bde+16precise) but it is not going to be installed
        Recommends: qgis-plugin-grass but it is not going to be installed
        Recommends: qgis-plugin-globe but it is not going to be installed
        Recommends: python-qgis but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I have had a look with synaptic package manager and wasnt able to track down any broken packages to do with QGIS.

---

### Post by steeldriver on 2016-05-09
What PPA specifically, and how exactly did you add it? What is your Ubuntu version?

It's suspicious that the GPG error appears to refer to 'precise' when the 'Hit' message says 'wily-security'

---

