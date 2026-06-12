---
title: "Google Chrome and SHA2"
date: 2016-06-09
forum: General Help
---

### Post by Hewjr100 on 2016-06-09
Currently in Ubuntu 16.04 Google Chrome was using SHA1 and update had error message about weak key.  Has the Google repo been updated to SHA2.  I deleted Google Chrome and am waiting for this to happen.

Henry

---

### Post by X-RED_Tech on 2016-06-09
You don't need to delete it.

---

### Post by Hewjr100 on 2016-06-09
Ok I will reinstall it, but will it update?

Henry

---

### Post by PaulW2U on 2016-06-09
> **Hewjr100 said:**
> Currently in Ubuntu 16.04 Google Chrome was using SHA1 and update had error message about weak key.
These are **WARNINGS**, not errors.
```
**W**: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
```
The issue has been fixed for the official Ubuntu PPAs - [https://bugs.launchpad.net/launchpad/+bug/1556666](https://bugs.launchpad.net/launchpad/+bug/1556666) but it seems that Google have still to update their own repositories.

[Dropping SHA-1 support in APT]("https://juliank.wordpress.com/2016/03/14/dropping-sha-1-support-in-apt/") should explain what you're seeing right now.

---

### Post by X-RED_Tech on 2016-06-09
Despite the warnings it's been updating on mine.

---

