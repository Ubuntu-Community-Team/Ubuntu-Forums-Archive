---
title: "has anyone got the new kde menu working (download link inside)"
date: 2006-09-23
forum: General Help
---

### Post by slimdog360 on 2006-09-23
they provide a .deb file here
[http://linux.softpedia.com/progDownload/KBFX-Download-11484.html]("http://linux.softpedia.com/progDownload/KBFX-Download-11484.html")

and the original site here
[http://news.softpedia.com/news/KBFX-A-new-KDE-menu-21849.shtml]("http://news.softpedia.com/news/KBFX-A-new-KDE-menu-21849.shtml")

I cant get it to install though, here is what I get

```
root@2[nick]# dpkg --install kbfx_0.4.9.1-ubuntu-breezy_i386.deb
Selecting previously deselected package kbfx.
(Reading database ... 102708 files and directories currently installed.)
Unpacking kbfx (from kbfx_0.4.9.1-ubuntu-breezy_i386.deb) ...
dpkg: dependency problems prevent configuration of kbfx:
 kbfx depends on kdelibs4c2 (>= 4:3.4.3); however:
  Package kdelibs4c2 is not installed.
dpkg: error processing kbfx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kbfx

```


Ive also tried compiling from source using the code on from the second link. When I get to the second step ```
./configure --prefix=`kde-config --prefix`
```
I get ths happen right at the end
```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

---

### Post by wieman01 on 2006-09-23
You need to install package "kdelibs4c2" first:
> sudo apt-get install kdelibs4c2
Got it running a while ago but dropped it because I think the default menu is alright.

---

### Post by slimdog360 on 2006-09-23
already tried it but I get this
```
root@2[nick]# apt-get install kdelibs4c2
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs4c2: Depends: libarts1c2 (>= 1.3.2) but it is not going to be installed
              Depends: libopenexr2c2 (>= 1.2.2) but it is not going to be installed
              Depends: kdelibs-bin (= 4:3.4.3-0ubuntu1) but 4:3.5.3-0ubuntu0.1 is to be installed
  kdelibs4c2a: Conflicts: kdelibs4c2 but 4:3.4.3-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by wieman01 on 2006-09-23
Are you still using KDE v3.4? There is a version conflict and I reckon you have to update KDE to the most recent version. Could you upgrade the mentioned packages (e.g. kdelibs-bin)?

---

### Post by slimdog360 on 2006-09-23
thanks for the response but it seems to have solved its self somehow. I wouldnt have a clue what happened but now its installed. Its a bit buggy though.

---

### Post by wieman01 on 2006-09-23
> **slimdog360 said:**
> thanks for the response but it seems to have solved its self somehow. I wouldnt have a clue what happened but now its installed. Its a bit buggy though.
I uninstalled it because of its random behavior & because it does not integrate well into KDE. But see for yourself...

---

