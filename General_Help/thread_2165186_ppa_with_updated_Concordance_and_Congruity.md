---
title: "ppa with updated Concordance and Congruity"
date: 2013-08-03
forum: General Help
---

### Post by paalfe on 2013-08-03
Anyone know of any ppa with updated Concordance and Congruity?

concordance 1.0 source was released at 2013-04-16.
[http://sourceforge.net/projects/concordance/](http://sourceforge.net/projects/concordance/)

congruity 17 source was released at 2013-06-12.
[http://sourceforge.net/projects/congruity/](http://sourceforge.net/projects/congruity/)

---

### Post by paalfe on 2013-08-10
**----------------------- Concordance and Congruity (GUI) - Logitech Harmony universal remotes START ----------------------- [http://www.phildev.net/harmony/]("http://www.phildev.net/harmony/") and [http://sourceforge.net/projects/concordance/]("http://sourceforge.net/projects/concordance/") and [http://sourceforge.net/projects/congruity/]("http://sourceforge.net/projects/congruity/") **

**NOTE:** Concordance 1.0 and Congruity 17 has been proposed (universe) for Ubuntu 13.10 (The Saucy Salamander). You find the packages here: [https://launchpad.net/ubuntu/+source/concordance]("https://launchpad.net/ubuntu/+source/concordance") and [https://launchpad.net/ubuntu/+source/congruity/ ]("https://launchpad.net/ubuntu/+source/congruity/")

**INFO:** Congruity is intended to process files provided by the Logitech(R) Harmony(R) configuration website, currently [http://members.harmonyremote.com]("http://members.harmonyremote.com"). You should configure your web browser to execute Congruity whenever a file of type EZHex, EZUp, or EZTut is downloaded.

```


**if 32bit - **[COLOR="#006400"]wget https://launchpadlibrarian.net/147212333/concordance_1.0-1_i386.deb -O concordance_1.0-1_i386.deb[/COLOR]
**if 32bit - **[COLOR="#006400"]wget https://launchpadlibrarian.net/147212335/libconcord-dev_1.0-1_i386.deb -O libconcord-dev_1.0-1_i386.deb[/COLOR]
**if 32bit - **[COLOR="#006400"]wget https://launchpadlibrarian.net/147212334/libconcord3_1.0-1_i386.deb -O libconcord3_1.0-1_i386.deb[/COLOR]

**if 64bit - **[COLOR="#8B4513"]wget https://launchpadlibrarian.net/147212222/concordance_1.0-1_amd64.deb -O concordance_1.0-1_amd64.deb[/COLOR]
**if 64bit - **[COLOR="#8B4513"]wget https://launchpadlibrarian.net/147212224/libconcord-dev_1.0-1_amd64.deb -O libconcord-dev_1.0-1_amd64.deb[/COLOR]
**if 64bit - **[COLOR="#8B4513"]wget https://launchpadlibrarian.net/147212223/libconcord3_1.0-1_amd64.deb -O libconcord3_1.0-1_amd64.deb[/COLOR]

wget https://launchpadlibrarian.net/147212337/concordance-common_1.0-1_all.deb -O concordance-common_1.0-1_all.deb
wget https://launchpadlibrarian.net/147212336/python-libconcord_1.0-1_all.deb -O python-libconcord_1.0-1_all.deb
wget https://launchpadlibrarian.net/147212582/congruity_17-1_all.deb -O congruity_17-1_all.deb

sudo apt-get install python-suds
sudo dpkg -i concordance*.deb python-libconcord*.deb libconcord*.deb congruity*.deb
sudo apt-get install -f


```

**------------------------- Concordance and Congruity (GUI) - Logitech Harmony universal remotes END ------------------------**

---

