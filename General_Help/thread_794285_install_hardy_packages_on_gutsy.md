---
title: "install hardy packages on gutsy"
date: 2008-05-14
forum: General Help
---

### Post by BackwardsDown on 2008-05-14
I am running Gutsy but I really want some program's that are only available in hardy (FF3, OO.org 2.4, latest pidgin, emesene, etc). But I dont know what the preferred method is to install these packages. Download them manually from packages.ubuntu.com, or temporaraly add the hardy sources to my source.list?

---

### Post by inportb on 2008-05-14
They should be the same. But if you want to have automatic dependency resolution and stuff, using hardy sources might be easier.
Can you find Gutsy versions through GetDeb?

---

### Post by dicecca112 on 2008-05-14
Pidgin can be downloaded from getDeb and works fine.  Firefox 3b5 should work without having to get it from Hardy.  Should be able to download the tar.gz and install it

---

### Post by kellemes on 2008-05-14
> **BackwardsDown said:**
> I am running Gutsy but I really want some program's that are only available in hardy (FF3, OO.org 2.4, latest pidgin, emesene, etc). But I dont know what the preferred method is to install these packages. Download them manually from packages.ubuntu.com, or temporaraly add the hardy sources to my source.list?

Using the Hardy sources will kill your system! Unless you go Hardy all the way.
You can either download the deb's from the developers webpage and install by hand.
Or you can use [backports]("https://help.ubuntu.com/community/UbuntuBackports").
I know ff 3+ is available from the backports, don't know about oo 2.4
[Search here]("http://packages.ubuntu.com/gutsy-backports/").

---

