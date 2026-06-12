---
title: "Failed to Download Repository Information"
date: 2012-12-09
forum: General Help
---

### Post by scpatl4now on 2012-12-09
I just started receiving this error about a week ago.  I have changed the server twice (letting it find the best server).  This is the error
```
W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Any ideas to go about fixing this?

---

### Post by gandaran on 2012-12-09
the getdeb server has been down for about a week now, you cant even get to the getdeb webpage! either wait or disable temporary the repository in sources list to avoid the errors.

---

### Post by scpatl4now on 2012-12-09
found work around here
[http://ubuntuforums.org/showthread.php?t=2092024](http://ubuntuforums.org/showthread.php?t=2092024)
just sub in for whatever you are running

---

### Post by SmilePiper on 2012-12-09
I've noticed that dotdeb.com has a few of the same games as on getdeb.

---

