---
title: "Can't run gWakeOnLan on 16.04 LTS"
date: 2016-05-15
forum: General Help
---

### Post by boz_1812 on 2016-05-15
Hi,

I recently did a clean install of Ubuntu 16.04 LTS.  This PC's BIOS has WOL enabled and was successfully used under 14.04 LTS.
I downloaded and installed gWakeOnLan via the terminal and running "apt list --installed" shows the package as installed.
I wanted to drag the icon to the launch bar, but when I search using the Dash, it's not listed among Applications, nor is it listed in the Software Centre.
Is gWakeOnLan compatible with 16.04?  It worked fine on 14.04.

Thanks.

---

### Post by deadflowr on 2016-05-16
It's messed up.
See this bug:
[https://bugs.launchpad.net/ubuntu/+source/gwakeonlan/+bug/1513567]("https://bugs.launchpad.net/ubuntu/+source/gwakeonlan/+bug/1513567")

As for any consolation wakeonlan functions correctly, but of course that misses the point, I guess.

---

### Post by boz_1812 on 2016-05-16
That explains it. 
I wasn't aware of wakeonlan (from the terminal).  I installed and tried it and it works perfectly.  
Thanks.

---

