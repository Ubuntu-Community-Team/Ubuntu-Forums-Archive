---
title: "Openconnect Issues"
date: 2015-03-26
forum: General Help
---

### Post by John_Everden on 2015-03-26
Hello everyone in a bit of a bind. I attempted to upgrade openconnect to 6 from 5.0.2-1. I downloaded and ran make and make install and it complained about dependencies. Afterwards I removed it and openconnect 5 using apt-get. I also ran purge. I then reinstalled using apt-get. I now get the following error:

error while loading shared libraries: libopenconnect.so.3: cannot open shared object file: No such file or directory and can no longer run it from command line. 

Additionally when connecting to anyconnect office VPN after using it very briefly I get a Dead Peer Detection error and can no longer visit local (local to the vpn) or external pages. This does not occur when using windows, or when using ubuntu connecting via my phone (instead of home network). I found this post which describes exactly what I was experiencing. [http://ubuntuforums.org/showthread.php?t=2181893](http://ubuntuforums.org/showthread.php?t=2181893)

If anyone has the time to help me it would much appeciated :)

Edit forgot to mention I am on ubuntu 14.04 Gnome

---

