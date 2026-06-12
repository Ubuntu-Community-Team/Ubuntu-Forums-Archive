---
title: "Unable to connect to in.archine.ubuntu.com"
date: 2020-06-27
forum: General Help
---

### Post by abhishek2602 on 2020-06-27
Getting this error when I try to use the command
sudo apt-get update

Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]      
Err:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal InRelease                      
  Could not connect to in.archive.ubuntu.com:80 (2403:8940:ffff::f). - connect (101: Network is unreachable) Could not connect to in.archive.ubuntu.com:80 (103.97.84.254), connection timed out
Err:6 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates InRelease
  Unable to connect to in.archive.ubuntu.com:http:
Err:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports InRelease
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 107 kB in 31s (3,489 B/s)
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/focal/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/focal/InRelease)  Could not connect to in.archive.ubuntu.com:80 (2403:8940:ffff::f). - connect (101: Network is unreachable) Could not connect to in.archive.ubuntu.com:80 (103.97.84.254), connection timed out
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease)  Unable to connect to in.archive.ubuntu.com:http:
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease)  Unable to connect to in.archive.ubuntu.com:http:
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by CelticWarrior on 2020-06-27
Welcome.

The problem is likely temporary so try again later. Or change to another server.

---

### Post by deadflowr on 2020-06-27
Try a different mirror:
Edit the sources, see:
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

Find a working mirror from the mirror listings here:
[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

---

