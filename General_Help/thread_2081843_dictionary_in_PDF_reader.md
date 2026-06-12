---
title: "dictionary in PDF reader?"
date: 2012-11-07
forum: General Help
---

### Post by opfeld on 2012-11-07
I am using Ubuntu 12.04 and using the standard Document Viewer 3.4 it comes with for reading PDF's.  Is there any way to set it up so that if I highlight a word I can search its definition from Document Viewer?  Or if not is there another PDF reader that has this capability?

---

### Post by uzumakifahim on 2012-11-07
You can try **Okular** and **Calibre**, they are much more feature rich than Document Viewer.

Thanks.

---

### Post by stinkeye on 2012-11-07
A simple way to do this is to install **artha**, an off-line thesaurus.
```
sudo apt-get install artha
```
or latest ppa version.(Can show meaning in notification bubble instead of bringing up the artha window.)
[**_[COLOR="DarkRed"]http://artha.sourceforge.net/wiki/index.php/Download#PPA[/COLOR]_**]("http://artha.sourceforge.net/wiki/index.php/Download#PPA")

Highlight a word in any application and press ctr+alt+w to bring it up.
[ATTACH]226863[/ATTACH]  [ATTACH]226860[/ATTACH]
 


If you want the indicator icon to show in unity you need to add it to
the systray-whitelist in dconf.
An easy way to do this is using **unsettings**.
Install unsettings via a ppa...
```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

**[SIZE="3"]or[/SIZE]**
...download Unsettings without adding the PPA, from
[**_[COLOR="DarkRed"]unsettings_0.08ubuntu1_all.deb[/COLOR]_**]("http://florian-diesch.de/software/unsettings/dist/unsettings_0.08ubuntu1_all.deb")
[ATTACH]226864[/ATTACH]

---

### Post by opfeld on 2012-11-08
awesome artha works great thanks for the help

---

