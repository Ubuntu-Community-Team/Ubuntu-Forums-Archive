---
title: "Weak digest algorithm"
date: 2017-09-16
forum: General Help
---

### Post by anshu68 on 2017-09-16
Description:	Ubuntu 16.04 LTS
Release:	16.04


While I run **$ sudo apt-get update **I'm getting this error message regarding weak digest algorithm. Please help.

W: [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg:](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg:) Signature by key C47415DFF48C09645B78609416126D3A3E5C1192 uses weak digest algorithm (SHA1)
W: [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/InRelease:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)

---

### Post by deadflowr on 2017-09-16
It's a warning not an error.
see if running
```
sudo apt upgrade
```
fixes it for you.

---

### Post by ajgreeny on 2017-09-16
Are you sure you're on 16.04 as the warnings say you are trying to download from precise (12.04) repos?

If so that may be your answer as that version is no longer supported so remove them from your /etc/apt/sources.list file.

---

