---
title: "How to use maildir format in evolution"
date: 2008-07-08
forum: General Help
---

### Post by mexlinux on 2008-07-08
Hi:
I know that evolution can read from a shared maildir.
But how can I set evolution to store all it's messages in maildir format.

Email is my main working tool and the evolution mailbox gets corrupted very often, maildir is more safe, how can I use it?

Thanks

---

### Post by mexlinux on 2008-08-01
If soeone cares, got this from the evolution mailing list:

El vie, 01-08-2008 a las 00:36 +0200, Philipp Riegger escribió:
> Having a file with about 1 GB is not that robust, and almost all
> incremental backup methods store the new version of this file every
> time.

This two simple arguments should be enought to consider maildir as
default for evolution

---

### Post by CSMatt on 2010-01-15
I apologize for bumping up such an old thread, but I too would like an answer to this question.

---

### Post by dcstar on 2010-01-16
> **CSMatt said:**
> I apologize for bumping up such an old thread, but I too would like an answer to this question.

The answer is you cannot.

I doubt there are any e-mail clients that "allow" you to store data in a format of your choosing, they all seem to use whatever they are designed to.

---

### Post by mexlinux on 2010-01-20
David:
the kmail applicaion from kontact in KDE let's you choose whatever format you want.

---

### Post by HeinzGas on 2010-02-19
In Evolution you can create a new account with Server type "Maildir" and point it to a location in your file system.

Heinz.

---

### Post by dcstar on 2010-02-20
> **HeinzGas said:**
> In Evolution you can create a new account with Server type "Maildir" and point it to a location in your file system.


That is **not** storing information, that is fetching e-mails from a Maildir location.

All data in Evolution is stored in it's database.

---

