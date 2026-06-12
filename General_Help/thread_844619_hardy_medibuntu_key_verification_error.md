---
title: "hardy medibuntu key verification error"
date: 2008-06-29
forum: General Help
---

### Post by scholzilla on 2008-06-29
I'm getting this when I run my update manager:

```
GPG error: http://ftp.debian-ports.org sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0792182443229C06GPG error: http://packages.medibuntu.org hardy 
Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://ftp.debian-ports.org/debian/dists/sid/main/binary-i386/Packages.gz  404 Not Found
```

any notions?

thanks

---

### Post by Wobblybob on 2008-06-29
you could try opening [System], [Admin..], [Software Sources] going to the 3rd party tab and deleting the medibuntu options then [ok] out and re add them in a [Terminal] by copy & pasting the following:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
and pressing [Enter], then
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
and again pressing [Enter]

---

