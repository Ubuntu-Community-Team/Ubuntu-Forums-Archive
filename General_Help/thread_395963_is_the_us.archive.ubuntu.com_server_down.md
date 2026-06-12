---
title: "is the us.archive.ubuntu.com server down?"
date: 2007-03-28
forum: General Help
---

### Post by rezell on 2007-03-28
title says it all. I cannot connect to it through apt or synaptic. I edited apt sources list and changed all references to it to de.archives ubuntu.com and it works fine. What gives??

here is what i get when I apt-get update

~$ sudo apt-get update
Err http: edgy Release.gpg
  Unable to connect to  http:
Ign http: edgy Release
Ign http: edgy/main Sources
Ign http: edgy/restricted Sources
Err http: edgy/main Sources
  Unable to connect to  http:
Err http: edgy/restricted Sources
  Unable to connect to  http:
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [189B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
99% [Waiting for headers]
 and it hangs there.
any help would be greatly appreciated.:)

---

### Post by IcemanV9 on 2007-03-28
Unfortunately, that is nothing new with US server being down. I switched to another mirror last week. I don't think I will go back to US anymore. It has been like that for a long time. :(

---

### Post by rezell on 2007-03-29
iceman, thanks for the reply. could you point me to a mirror in the us?
robert

---

### Post by orb9220 on 2007-03-29
There is only the one. Change synaptic to use UK or one of the others much faster.

Being a US server does not mean it is faster by default. Since US servers have a higher load than let's say canada or UK as an example.

---

### Post by rezell on 2007-03-29
thanks orb9220
I'll do that.
robert

---

