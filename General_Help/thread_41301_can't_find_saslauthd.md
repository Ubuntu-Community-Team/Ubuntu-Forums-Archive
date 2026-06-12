---
title: "can't find saslauthd"
date: 2005-06-12
forum: General Help
---

### Post by cbqwinner on 2005-06-12
Found the problem on another thread.  The problem was the repositories for us.archive.ubuntu.com are flaky and removing the us made everything work.   Of course I find this out after I blow everything away and start from scratch, but at least this time I'm keeping better notes.

I'd like to extend a hearty thank you to the 3 people who looked at this thread.   i really feel the love around here.  No really...

I'm have an email server up and running fine with Postfix, amavisd-new and clamav.  I'm only using local accounts so far and i'm trying to setup cyrus sasl so i can do imap and pop.

I've been following [this](http://flurdy.com/docs/postfix)  sort of.  I've installed  following cyrus packages
      libsasl2
      libsasl2-modules
      libsasl-modules-plain
      libsasl7
      libauthen-sasl-perl
      libauthen-sasl-cyrus-perl

My problem is I can't find saslauthd to start it.  I've checked ps -LA and don't see it running at all.  Doing whereis, comes back with nothing.  I've checked /etc/init.d and a few other spots.

Any suggestions would be great.  Thanks

---

### Post by obaeko on 2005-07-11
I have the same problem. Saslauthd is not in my system at all!!! Can any one help us???

---

### Post by jarek on 2005-07-16
[QUOTE=obaeko]I have the same problem. Saslauthd is not in my system at all!!! Can any one help us???[/QUOTE]

install sasl2-bin package (it MAY be in universe resp. only). It contains sasl2 binaries (incl. saslauthd).

---

### Post by obaeko on 2005-07-21
Thanks, that did the job. :-)

---

### Post by dcostelloe on 2005-10-15
have the same issue need these:

 libsasl-modules-plain
libsasl7

anyone know where I can get them?

No help anywhere else

---

