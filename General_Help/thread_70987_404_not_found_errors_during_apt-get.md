---
title: "404 not found errors during apt-get"
date: 2005-10-01
forum: General Help
---

### Post by mog27 on 2005-10-01
Tonight while doing an apt-get update; apt-get upgrade, I get this:

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found

Is something wrong? Are those repos down??

---

### Post by GreyFox503 on 2005-10-02
I've noticed this too.  I haven't found a solution yet, but I think the backports servers are changing and are going to be officially part of ubuntu.  Or perhaps this has something to do with getting ready for Breezy?

I still don't know what to change the repo's to.  Maybe someone else can enlighten us...

---

### Post by tehwa on 2005-10-02
See this thread:

[http://www.ubuntuforums.org/showthread.php?t=69681](http://www.ubuntuforums.org/showthread.php?t=69681)

---

### Post by GreyFox503 on 2005-10-02
Thanks for pointing me to that thread, but I'm still not able to use the new official backports... not sure what I'm doing wrong.

EDIT:  I figured it out.  I was opening up Synaptic and it kept giving me errors about the new backports.  However, do this:

sudo apt-get update

from the terminal.  I did that, it downloaded the lists with no errors, and now I can load synaptic again without problems.

---

### Post by darkmatter on 2005-10-02
[QUOTE=GreyFox503]Thanks for pointing me to that thread, but I'm still not able to use the new official backports... not sure what I'm doing wrong.[/QUOTE]

Please post the contents of your /etc/apt/sources.list.

---

### Post by GreyFox503 on 2005-10-02
Thanks for the fast reply, darkmatter.  (five minutes!?!)

I was able to fix it (must have been a synaptic bug or something) but I'm using the new backports now.  See my edited thread above.

---

### Post by darkmatter on 2005-10-02
[quote=GreyFox503](five minutes!?!)[/quote]
That's the Ubuntu Forums for ya';)

Glad to hear that you've got everything working.

---

