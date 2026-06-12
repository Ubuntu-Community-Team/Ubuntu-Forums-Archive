---
title: "No Yahoo Messenger?"
date: 2006-11-09
forum: General Help
---

### Post by browndog on 2006-11-09
Hi everyone,

I'm having an impossible time trying to get Yahoo Messenger to work.  When I try to install it I get the following error message:

```
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
```

I have enabled all of the repositories in the Synaptic package manager, and have installed every file I can find that is related to xlibs.  Also, libssl0.9.6 is nowhere to be found, but I did find and install libssl0.9.7.  Nothing worked.  Any help for it or am I hosed?

---

### Post by iamhugeinjapan on 2006-11-09
Did you download that deb from Yahoo? It looks extremely old. The dependencies it wants are possibly too old to run anymore.

That version of Yahoo might have less features than the Gaim implementation anyway. There is a good effort at a current Yahoo Messenger clone but the name escapes right now

---

### Post by Sef on 2006-11-09
Check out [GyachI]("http://gyachi.sourceforge.net/").  It's a yahoo clone.

Ubuntu comes with GAIM and Kubuntu comes with Kopete both which clone msn, yahoo, jabber, aim and others.

---

### Post by browndog on 2006-11-09
Thanks so very much to the both of you for your posts.  I'll probably stick with Gaim or the GyachI clone, since Yahoo hasn't seen fit to produce an updated and viable IM for Linux.

---

### Post by Midway on 2006-11-09
The last time I tried YIM Linux it looked like something out of Win95, lol.  Gaim is much more pleasant looking.

---

### Post by lowracer on 2006-11-09
I have a bunch of contacts on IM and none of them can agree on which system to use, Yahoo, AIM, MSN, etc.  So programs like Gaim or Kopete which handle multiple IM systems are a requirement for me.

---

