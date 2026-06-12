---
title: "Problem with update from volatile sources"
date: 2007-10-18
forum: General Help
---

### Post by btaylor101 on 2007-10-18
After adding the Debian volatile source to /etc/apt/sources.list I am getting the following error when performing sudo apt-get update:

> W: GPG error: [http://volatile.debian.org](http://volatile.debian.org) etch/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC61E0B0BBE55AB3
W: You may want to run apt-get update to correct these problems

The source I added was:
> deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free

---

### Post by rbmorse on 2007-10-18
I won't comment on whether what you are trying to do is particularly wise or not, you need to reinstall the public key for that repository.  The site's main page should have a pointer.

---

### Post by btaylor101 on 2007-10-18
I am using it only for update to ClamAV. Is there a way to only have ClamAV look in this repository?

---

