---
title: "Deluge user Permission denied on USB HDD"
date: 2013-01-30
forum: General Help
---

### Post by mafi127 on 2013-01-30
I have installed deluge headless using this tutorial [http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)

I have greated a new user to deluge and allso flexget, everything works fine but when flexget adds something to deluge then it says in status

```
"Permission denied: /media/2TB/downloads/"
```I have 2 external HDD's one is 2TB and another is 3TB. I want to download my files to 2TB and then flexget move extracted files to 3TB HDD, but deluge user dosent have premision to write thows HDDs.

I have tryed using

```
 chown -hR deluge:users /media/2TB
```it works but then aigan the owner of hdds is deluge, and my samba share dosent work aigan.

can some1 help me out whit this

--- EDIT --

Got problem fixed using 

 chown -hR deluge:users /media/2TBDident add  my username to other user, my mistake :)

---

