---
title: "I can't install Wine"
date: 2005-09-03
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-03
Everytime a try to install wine by "sudo apt-get install wine", the download of the files start with a high velocity. Then, the download gets slower and slower, until I get the following message:
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.0.20050725-winehq-1 [14.9MB]
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.0.20050725-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.0.20050725-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.0.20050725-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What should I do?
PS: I've already used apt-get update and I've already tried to use sudo apt-get install wine --fix-missing (I got the same error message).

---

### Post by Maier on 2005-09-03
try from another repository.. 

try to add some xtra.. all the ones for ubuntuguide, and the xtras for my language helped me install win smoothly.. :)

---

