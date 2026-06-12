---
title: "Update Manager"
date: 2005-06-22
forum: General Help
---

### Post by jkrolen5500 on 2005-06-22
I use my own kernel because I like to.  Therefore I do not want the update manager telling me that I need linux-image-2.6.10-5-386.  I have tried putting the following in /etc/apt/preferences:

Package: linux-image
Pin: version 2.6.10-5-386*
Pin-Priority: 1001


That did not work.  How do I configure apt to stop harassing me and show a green check showing im up to date?

Secondly I get this error:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

I added an untrusted site and don't care that it can't be verified.  How do I ignore that warning ?

---

### Post by dabear on 2005-06-22
Please read this: [http://ubuntuforums.org/announcement.php?f=58](http://ubuntuforums.org/announcement.php?f=58)

---

