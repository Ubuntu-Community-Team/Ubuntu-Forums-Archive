---
title: "Crippling error /bin/sh cant access tty etc"
date: 2007-12-05
forum: General Help
---

### Post by Sugz on 2007-12-05
This is a duplicate of the thread i made elsewhere.
I am using Wubi and now it does not start up instead it gets to around 10% and the following error is display 

C/bin/sh cant access tty: jb control turned off

Please help as this is preventing me from using Wubi and therefore Ubuntu. and im stuck with Vista :-(

Please any help appreciated

---

### Post by ago on 2007-12-05
This has been addressed a few times in the past, you may want to search the forum.
Also note the wubi version you are using.

---

### Post by jimbo99 on 2007-12-06
I repeatedly searched the forums for his error message, and even just some keywords.  I found absolutely zero hits.

As a long term user of these forums I would ask that you respect the posters and either give them the links or answer the questions.  Please do not direct them to search when you yourself didn't try.  If you had you would have found no hits.

Aside from that you are doing a good job. But please remember we are here because we are humans using Linux and not a machine the spews things back in rote.

---

### Post by n3hu on 2008-01-11
same problem here tonight.... booted up
using an "ultimate boot cd for windows"
and ran chdsk /f. All was well after that.
I did NOT but could also have ran the
longer "chkdsk /r" option since the /f
fixed it.

---

### Post by ago on 2008-01-11
> **jimbo99 said:**
> I repeatedly searched the forums for his error message, and even just some keywords.  I found absolutely zero hits.

searching the wubi forum for "tty" I get 250 posts...

Anyway, as suggested above try "chkdsk /r" from windows first, if you are using wubi-cdboot (the one that ship with the CD) make sure the CD is inserted.  For anything else see if there are logs:

/casper.log
/tmp/initramfs*

You can have more verbose output/logs by hitting esc at the countdown and selecting verbose mode.

---

### Post by Sugz on 2008-01-12
oh i appoligise, this problem has been resolved, thank you for your help
-Sugz

---

