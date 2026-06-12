---
title: "Aptitude GPG error"
date: 2007-02-15
forum: General Help
---

### Post by quiller on 2007-02-15
For the past few days, whenever I try to run an update in command-line or the GUI, I get this error:

```
W: GPG error: http://debian-multimedia.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
```
I tried to get the key from the instructions on debian-multimedia.org, but I still get this error. The only thing I've changed is changing the source to "stable" from "sarge." I don't know what that refers to, but the error is the same either way.

---

### Post by bapoumba on 2007-02-15
If you want to install codecs, you may want to check the [medibutu repos]("http://medibuntu.sos-sts.com/"), which packages softwares for Ubuntu (and comment out the debian repo from your sources.list).

---

### Post by quiller on 2007-02-15
Thanks! Followed their instructions and I was able to update; it even upgraded the exact packages I was trying to update before. Good suggestion!

---

