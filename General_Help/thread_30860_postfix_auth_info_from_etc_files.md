---
title: "postfix auth info from /etc files"
date: 2005-04-30
forum: General Help
---

### Post by robshep on 2005-04-30
I removed all trace of the postfix user and groups info from my hoary.

I'd like to put them back now Doh!

If anybody has a fairly fresh install could they post the lines from

/etc/passwd:
postfix

/etc/group:
postfix
postdrop

/etc/shadow:
postfix

Cheers v. much

Rob

---

### Post by robshep on 2005-05-02
I found /etc/passwd- and /etc/group- files from the configuration of GDM, these contained the information I needed.

---

