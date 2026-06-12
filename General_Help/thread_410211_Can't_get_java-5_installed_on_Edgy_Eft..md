---
title: "Can't get java-5 installed on Edgy Eft."
date: 2007-04-15
forum: General Help
---

### Post by randell6564 on 2007-04-15
Hey folks!
I just upgraded to Edgy Eft last night.  I'm now trying to install LimeWire-Pro.  (I don't even HAVE to have limewire. I would settle for Frostwire).
I used the tutorial at ['TorrentFreak']("http://torrentfreak.com/") (sorry, the exact link is broken), but got this error:
> sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate
Can anyone help me through this?
Thanks!

---

### Post by randell6564 on 2007-04-15
Never mind folks!
I needed to go to System>Administration>Software Sources, enable Multiverse, and do:
```
sudo apt-get update
```
Then do:
```
 sudo apt-get install sun-java5-jre sun-java5-plugin
```
Alls well at this point!

---

