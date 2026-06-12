---
title: "wily-updates ~ Hash Sum mismatch"
date: 2016-02-17
forum: General Help
---

### Post by neu5eeCh on 2016-02-17
For no apparent reason, updating this morning resulted in:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages)  Hash Sum mismatch


Anyone know what's up? I tried the following from askubuntu:

```
sudo rm -rf /var/lib/apt/lists/*
```
  
```
sudo apt-get update
```



But no satisfaction.

---

### Post by neu5eeCh on 2016-02-17
And for no apparent reason, it seems to have fixed itself? So... never mind.

---

