---
title: "Ubuntu Xenial LTS fail to fetch updates"
date: 2018-01-29
forum: General Help
---

### Post by athornfam2 on 2018-01-29
I thought I would reach out to everyone in the Ubuntu forums to see if someone can enlighten me on this issue. So out of the blues i've been getting this issue below... Its happened on two machines... not sure if anyone has any suggestions. For more information what I've already performed please look at this thread [https://community.spiceworks.com/topic/2102742-problems-with-apt-get-update-xenial-lts?page=1](https://community.spiceworks.com/topic/2102742-problems-with-apt-get-update-xenial-lts?page=1) 

```
Err:1 http://archive.canonical.com/ubuntu xenial InRelease  Could not connect to archive.canonical.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80]
Err:2 http://archive.ubuntu.com/ubuntu xenial InRelease
  Could not connect to archive.ubuntu.com:80 (91.189.88.162). - connect (111: Connection refused) [IP: 91.189.88.162 80]
Err:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Err:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not connect to archive.ubuntu.com:80 (91.189.88.162). - connect (111: Connection refused) [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.162 80]
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/InRelease  Could not connect to archive.canonical.com:80 (91.189.91.15). - connect (111: Connection refused) [IP: 91.189.91.15 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by coffeecat on 2018-02-02
Closed.

[Duplicate](https://ubuntuforums.org/showthread.php?t=2384138) posted.

---

