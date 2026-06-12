---
title: "testing a patch :  correctly applying .debdiff?"
date: 2007-10-29
forum: General Help
---

### Post by bwayne on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/153152](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/153152) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.  I filed a [bug]("http://https://bugs.launchpad.net/bugs/153152") against hplip.  The developer posted a patch in the form of a .debdiff which he says worked on his machine.  After finding [instructions]("http://https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff") for applying a patch via a .debdiff and then applying it, I found that the patch didn't work for my machine.  

I wanted to post what I had done here before I reported the failure back to launchpad.  This is the first time I've ever applied a patch and I wanted a second opinion on what I was doing.


Below is what I've done.  

```
root@earth:~# wget --no-check-certificate https://www.linux-foundation.org/~till/tmp/ubuntu/gutsy/hplip/hplip_2.7.7.dfsg.1-0ubuntu5_2.7.7.dfsg.1-0ubuntu5.1.debdiff    

root@earth:~# apt-get source hplip

root@earth:~# apt-get build-dep hplip

root@earth:~# cd hplip-2.7.7.dfsg.1/

root@earth:~# patch -p1 < ../*.debdiff

root@earth:~# debuild -uc -us

root@earth:~# dpkg -i ../*.deb
```

After doing this procedure, the above bug is still present.  I think I may be doing something incorrectly since the dev on launchpad says that it worked for him.  

Any feedback appreciated.  


BWayne

---

