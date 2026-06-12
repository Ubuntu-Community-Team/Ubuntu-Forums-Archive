---
title: "Why is libgtk deb under main/g and not under main/libg?"
date: 2006-08-18
forum: General Help
---

### Post by jamadagni on 2006-08-18
I recently downloaded the deb of latest Firefox update, and when I try to do dpkg it said it needed libgtk, libatk and libpango as dependencies. So I search the pool for libgtk under libg, but it is not there. Similarly libatk and libpango are not under liba and libp. They are under main/g/, main/a/ and main/p/ respectively. I do not understand why this is. 

I thought that the Debian/Ubuntu pool classification system was wonderful compared to SUSE's practice of throwing 5000 RPMs into one dir (it takes quite some time for the file *list* to be displayed in Konqueror), but now I am quite confused.

When is a libx* package put under libx/ and when under x/ ? Thanks.

P.S: I know there is a better way to update firefox than downloading the debs manually, but I am forced to do this for some reasons.

---

### Post by fdoving on 2006-08-18
This is because it is sorted from the name of the source package.

Try:
'apt-cache show libgtk2.0-0'

You can see:
Source: gtk+2.0

- Frode

---

### Post by jamadagni on 2006-08-19
That is pretty obvious, but *why*? Why is libcairo not sorted according to the package name cairo but is placed [under libc]("ftp://ftp.ubuntu.com/ubuntu/pool/main/libc/libcairo")?

---

