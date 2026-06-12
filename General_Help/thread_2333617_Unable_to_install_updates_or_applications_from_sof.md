---
title: "Unable to install updates or applications from software center"
date: 2016-08-11
forum: General Help
---

### Post by yudio on 2016-08-11
Hi, I received a Dell Latitude D620 with Ubuntu 12.10 on it and it's unable to install anything including updates or applications from the software center. I am incredibly inexperienced with Linux and have seen this error when using the software updater:

```

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1360:8001::21 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

It also tells me to check my internet connection despite being connected. I've looked around on the internet and if it was possible to see if it was an issue with the software center, I had uninstalled it using terminal and cannot reinstall it, saying that "software center has no installation candidate."
Is there a way to I suppose "fix" the problem with being unable to install anything? If not is it possible to perform a reset as if it was just first time booting up?

---

### Post by QIII on 2016-08-11
Hello!

12.10 is well past its End Of Life (which was in July of 2013) and the repositories have been moved.  That is why you are getting the 404 (Not Found) messages.

I would suggest that you do a fresh install of a supported LTS version:  12.04, 14.04 or 16.04.  Of them, 14.04 might be the best.  It is supported until 2019 and may be less trouble than 16.04 at the moment.

Cheers!

---

### Post by yudio on 2016-08-18
All right, thank you very much!

---

### Post by mörgæs on 2016-08-18
If this solves your problem please mark the thread so.

For a 620 I recommend Lubuntu, not Ubuntu.

---

