---
title: "etckeeper not commiting after apt"
date: 2016-06-18
forum: General Help
---

### Post by el_baby on 2016-06-18
I've been using etckeeper for about 5 years to keep track of changes I make to config files (and to detect strange changes). I first used mercurial and, in the last year, I started using git for new installations.

I always make the following changes in order to see if I (or someone/thing else) changed anything since I last commited or installed something:

```
AVOID_DAILY_AUTOCOMMITS=1

AVOID_COMMIT_BEFORE_INSTALL=1

```

The most usual nuance is that CUPS insists on automatically changing [FONT=Courier New]/etc/cups/printer.conf[/FONT] by itself.

However, yesterday I installed etckeeper with git on my first 16.04 (a system76 lemur notebook) and it seems that it is NOT commiting AFTER it runs APT, as it always did.

Anyone can think what may be wrong?

TIA

---

### Post by el_baby on 2016-06-18
SORRY:

I forgot to configure the email in the git repository and that was making the [FONT=Courier New]git commit[/FONT] fail after running APT.

Funny thing is that I didn't follow my own instructions regarding that at [http://wiki.clueless.com.ar/EtckeeperConGitEnUbuntu](http://wiki.clueless.com.ar/EtckeeperConGitEnUbuntu)

---

