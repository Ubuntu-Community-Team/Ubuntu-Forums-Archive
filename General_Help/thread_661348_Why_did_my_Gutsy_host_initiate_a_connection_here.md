---
title: "Why did my Gutsy host initiate a connection here?"
date: 2008-01-07
forum: General Help
---

### Post by DugieHowsa on 2008-01-07
I was in the midst of trouble shooting a web site issue in firefox, when I saw my connection itiniate a connection to the following host:

DST HOST bluetack1.snowmanuk.net.nyud.net
DST PORT 8080

Weird.  So I entered it into firefox, and it redirected me to the following URL

[http://bluetack.snowmanuk.net:8000/](http://bluetack.snowmanuk.net:8000/)

Weird.  Its some type of torrent tracking web site.  Now, I'm not sure why my computer is trying to visit this site, but it has me slightly concerned.  Any thoughts as to how to track down the process that is doing this?  Is there a way to see if there is a setting in firefox that is causing this?  Perhaps due to some type of plug-in I installed?

---

### Post by kidders on 2008-01-09
Hi there,

Network connection information is all available in /proc. There are lots and lots of utilities that can parse it and present it in various different ways, for example, something like ...```
sudo watch -d netstat -ptW
```... should give you reasonably detailed real-time information about what your computer is talking to, including process information. (The "sudo" is necessary for access to PIDs.) Alternatively, you could throw together a script to notify you whenever a connection to the host you mentioned gets made, and tell you what initiated it.

Once you know what applications are involved in a suspicious internet connection, you'll hopefully have a clearer idea of what's going in.

---

### Post by DugieHowsa on 2008-01-10
Found my answer.  I was running Peer Guardian, and it pulled its updates from the web site.  Found the URL in the config section of the shell script.

---

