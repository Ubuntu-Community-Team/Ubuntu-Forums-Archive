---
title: "update Openssl"
date: 2014-04-24
forum: General Help
---

### Post by matimont on 2014-04-24
Hi,

I have an Ubuntu Server (12.04) and need to upgrade Openssl

When I run this:
openssl version

I get this:
OpenSSL 1.0.1 14 Mar 2012

Which I think is not the latest one, however, when I run this command:
apt-get install openssl

I get this:

openssl is already the newest version.

I thought 1.0.1f was the latest version so..

Thanks!

---

### Post by deadflowr on 2014-04-24
Run
```
openssl version -a
```
and look at the build date.
April 7 was when they release the patch to fix the heartbleed bug, if that is your concern.

---

### Post by matimont on 2014-04-24
This is what I get:
OpenSSL 1.0.1 14 Mar 2012
built on: Mon Apr  7 20:33:29 UTC 2014


So I'm ok

Thanks!

---

