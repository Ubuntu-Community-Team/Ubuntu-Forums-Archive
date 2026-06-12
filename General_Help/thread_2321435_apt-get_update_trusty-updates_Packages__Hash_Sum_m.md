---
title: "apt-get update trusty-updates Packages  Hash Sum mismatch"
date: 2016-04-22
forum: General Help
---

### Post by kuenn_leow on 2016-04-22
[B]ERROR while trying to "apt-get update"
[/B]

	:
W: Failed to fetch [http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  Hash Sum mismatch
W: Failed to fetch [http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages](http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages)  Hash Sum mismatch
W: Failed to fetch [http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Hash Sum mismatch
W: Failed to fetch [http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://10.0.0.98:9081/au.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  Hash Sum mismatch

MD5SUM confirmed my files are the same as the one on au.archive.ubuntu.com

any advice appreciated.

---

### Post by oldos2er on 2016-04-22
Try ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update
```

---

### Post by kuenn_leow on 2016-04-24
Solved, problem went away by itself after i rerun apt-mirror a day later.

---

### Post by sammiev on 2016-04-24
It seems to happen from time to time.

Usually you can run apt-get update a few hours later with no issues.

Please mark your thread as [solved] so to help others.

---

### Post by oygle on 2016-04-25
Yes, I got it this morning also ..

> 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  Hash Sum mismatch

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


Will try again in a few hours, as advised.  :)

---

