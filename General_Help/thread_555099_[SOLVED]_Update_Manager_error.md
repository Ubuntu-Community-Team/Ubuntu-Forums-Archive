---
title: "[SOLVED] Update Manager error"
date: 2007-09-19
forum: General Help
---

### Post by JIMW428 on 2007-09-19
[B]When running Update Manager, I receive the following error message:
[/B]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

Any ideas for a fix?

---

### Post by jamvegan on 2007-09-19
This:
```
sudo rm /var/lib/apt/lists/partial/*
```
generally seems to resolve that issue, which appears to be caused by a corrupted list of available packages.

---

### Post by JIMW428 on 2007-09-19
It took 2 tries but that worked! Many thanks!

---

### Post by adonikam on 2007-10-19
this also worked for me ....
could you send me more information about this solution? I want to understand it better.

also, i went on searching for a long time for this solution but it took a long time to find it. I did find a lot of other people with this problem, but they were mostly told it was due to "network congestion". Is there some way to make this solution more readily accessible?

---

