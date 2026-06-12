---
title: "Gallery2 and apache/apache2"
date: 2007-03-10
forum: General Help
---

### Post by weetbix on 2007-03-10
I just reinstalled my server with a fresh install of edgy from the server cd.  About the only thing installed on here that the cd didn't set up (as basic as it could get) is openssh-server.

My problem is that when I go to install gallery2 - no matter what I do it always seems to want to install both apache *and* apache2.  I have no problems with it installing a version of apache (infact I want it to install a version)  - but why is it trying to install 2 versions of apache when it only requires 1 version?

[http://packages.ubuntu.com/edgy/web/gallery2](http://packages.ubuntu.com/edgy/web/gallery2)

According to that page it depends on either version, not both.

You've probably guessed by now - but I would like only one version of apache installed if possible (I'm trying to keep the server as clean as I can) ... is this possible?

---

### Post by weetbix on 2007-03-11
Hmmm .... it appears as though my understanding of how dependancies work doesn't quite match reality.

I installed a version of apache (apache2 acually) and then went to install gallery2 again and it seemed to act a little more as I expected.  Oh well .....

---

### Post by llamakc on 2007-03-11
Installing apache2 will install the apache-common package, as others. You probably only installed one apache instance.

---

