---
title: "Ubuntu 6.0.6 - Firefox 1.5.0.10 after update"
date: 2007-03-09
forum: General Help
---

### Post by josir on 2007-03-09
Hi folks, 

Firefox stops to open certain SSL sites after last Ubuntu update. Example:

[www.gmail.com](www.gmail.com)
del.icio.us

Ubuntu 6.06 LTS - Kernel 2.6.15-28-386
Firefox 1.5.0.10

I've already searched other user's messages:

[http://forums.mozillazine.org/viewtopic.php?t=521803](http://forums.mozillazine.org/viewtopic.php?t=521803)
[http://forums.mozillazine.org/viewtopic.php?t=528484](http://forums.mozillazine.org/viewtopic.php?t=528484)

But I don't if those problems are related to mine.

Does someone has any tip to fix it?
What other info can I post to detail the problem?

Thanks in advance,
Josir.

---

### Post by IcemanV9 on 2007-03-09
I have 6.06.1 LTS (Dapper), 2.6.15-28-686 kernel and Fx (1.5.0.10) on my box.

I have no problem with gmail or del.icio.us. However, you could remove expired certificates from Edit > Preferences > Security tab > Certificates.

What was it being updated that you think it causes the problem with Fx? (check your log)

---

### Post by WW on 2007-03-09
josir,

Similar problems were reported in this thread: [http://ubuntuforums.org/showthread.php?t=374232](http://ubuntuforums.org/showthread.php?t=374232)

Skip the beginning of the thread; the discussion about ssl sites doesn't start until the second page of posts.

---

### Post by tagginannie on 2007-03-09
Try deleting your cookies and clearng the cache if that dose not work than Google is having server trouble

---

### Post by josir on 2007-03-09
Thanks for all replies.

About certificates: there is no certificates installed.

About logs: where can I find them?

About Google server trouble: all https sites are not working - it's not only gmail.

About [http://ubuntuforums.org/showthread.php?t=374232](http://ubuntuforums.org/showthread.php?t=374232) - the thread ends with a bug report (I cannot read because it also uses https...)

Any other suggestions will be welcome!
Josir.

---

### Post by DJ_Peng on 2007-03-10
You may want to upgrade to Firefox 2. Regardless of what caused this problem, Firefox 1.5.x is nearing the end of it's update lifespan. After 27 April there will be no more updates to the Firefox 1.5.x branch and Mozilla is recommending all users upgrade to Firefox 2. See [http://developer.mozilla.org/devnews/index.php/2007/02/23/firefox-2002-and-firefox-15010-security-and-stability-update/](http://developer.mozilla.org/devnews/index.php/2007/02/23/firefox-2002-and-firefox-15010-security-and-stability-update/) for more information.

---

### Post by IcemanV9 on 2007-03-13
@ DJ_Peng - If that is the case (Fx 1.5 + no more updates), then I hope Ubuntu maintainer updated Fx for Dapper (**Long Term Support**) from 1.5 to 2.x soon!

---

### Post by DJ_Peng on 2007-03-13
Me too, especially since Mozilla has been encouraging everyone to the 2.x branch since Firefox 2 came out in November. It would make sense, though, if Dapper has long term support.

---

