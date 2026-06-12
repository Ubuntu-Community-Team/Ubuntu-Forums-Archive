---
title: "index files filed to download?"
date: 2017-01-07
forum: General Help
---

### Post by Matrix01 on 2017-01-07
i see this "index files failed to download...................." every time Update ran.
Does this Lubuntu need to fix?


taro@taro-HP-Mini-110-3000:~$ sudo apt-get update
[sudo] password for taro: 
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease [491 B]
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [498 B]
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [499 B]     
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [501 B]
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Fetched 1,989 B in 0s (11.5 kB/s)
Reading package lists... Done
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Some index files failed to download. They have been ignored, or old ones used instead.
taro@taro-HP-Mini-110-3000:~$

---

### Post by vasa1 on 2017-01-07
See the various answers here: [http://askubuntu.com/questions/474549/got-nodata-issue-nodata-does-the-network-require-authentication](http://askubuntu.com/questions/474549/got-nodata-issue-nodata-does-the-network-require-authentication)

---

### Post by Matrix01 on 2017-01-15
anybody know how to fix this problems?

---

