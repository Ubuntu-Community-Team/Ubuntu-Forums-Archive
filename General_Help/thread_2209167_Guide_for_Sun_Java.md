---
title: "Guide for Sun Java"
date: 2014-03-04
forum: General Help
---

### Post by Mazate on 2014-03-04
Does anyone know of a good (simple) guide that can be used to install Oracle java?  Iced tea isn't quite working for what I'm using it for so I need the normal thing.  The guide on Oracle's site though isn't real clear.

---

### Post by phidia on 2014-03-04
Maybe this [wiki here]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") helps?

---

### Post by claracc on 2014-03-04
The easiest way to install oracle java and get the updates automatically is doing it through webup8 ppa.

Please see this link: [http://www.webupd8.org/2013/12/oracle-java-ppa-updated-with-arm-support.html](http://www.webupd8.org/2013/12/oracle-java-ppa-updated-with-arm-support.html) with full instructions.

---

### Post by Mazate on 2014-03-04
Thanks.  That's an excellent tutorial.  I installed Oracle Java yesterday and it didn't work and, judging from this tutorial I missed a few steps.  What would be the command to remove yesterday's installation?

---

### Post by QIII on 2014-03-04
To be honest, you might just as well leave yesterday's alone and not risk problems.  The webupd8 method will still install just fine and will set itself as the alternative used.  I'm not sure (I'm on my cell phone) but webupd8 may use the same directory to install to anyway.

---

### Post by Mazate on 2014-03-04
Any idea why the webupd8 instructions and the other wiki instructions are so vastly different?  The wiki instructions are long and detailed.

---

### Post by QIII on 2014-03-04
Because webupd8's PPA contains an installation package (somewhat like an Ubuntu repostory) that automates the process AND keeps you up to date when Oracle releases a new version.

webupd8 does not have the actual Oracle binaries (they can't, legally, because Oracle does not authorize that).  The installer automatically downloads the binaries from Oracle so you don't have to and then takes care of putting things in the right places, activating the browser plugin and setting the alternative to use.

webupd8 is one of the few organizations with PPAs that I trust.  I use PPAs very sparingly.

By the way, it's Oracle Java not Sun Java.  Oracle bought Sun several years ago.

---

### Post by Mazate on 2014-03-04
The problem I'm having is that when I try to reinstall it, it appears to think that it's already installed, plus I think it's loading the oracle repo instead of the weupd8 PPA.

---

