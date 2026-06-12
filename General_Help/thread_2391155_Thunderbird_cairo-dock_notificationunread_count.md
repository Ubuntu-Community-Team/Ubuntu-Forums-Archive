---
title: "Thunderbird cairo-dock notification/unread count"
date: 2018-05-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-05-06
For some reason it is not working on 18.04 but works on 17.10 despite the software version are still the same
This is the software i have on 18.04:
```
 apt-cache policy cairo-dock thunderbird
cairo-dock:
  Installed: 3.4.1-1.2
  Candidate: 3.4.1-1.2
  Version table:
 *** 3.4.1-1.2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
thunderbird:
  Installed: 1:52.7.0+build1-0ubuntu1
  Candidate: 1:52.7.0+build1-0ubuntu1
  Version table:
 *** 1:52.7.0+build1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```
this is the TB addon:
Cairo-Dock unread messages 1.0.5
this is what i have on 17.10:
```
thunderbird:
  Installed: 1:52.7.0+build1-0ubuntu0.17.10.1
  Candidate: 1:52.7.0+build1-0ubuntu0.17.10.1
  Version table:
 *** 1:52.7.0+build1-0ubuntu0.17.10.1 500
        500 http://us.archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu artful-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:52.4.0+build1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
cairo-dock:
  Installed: 3.4.1-0ubuntu1
  Candidate: 3.4.1-0ubuntu1
  Version table:
 *** 3.4.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu artful/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu artful/universe i386 Packages
        100 /var/lib/dpkg/status


```
this is the TB addon:
Cairo-Dock unread messages 1.0.5

---

### Post by pqwoerituytrueiwoq on 2018-05-07
For some reason i have a old version's file even thought i have the latest version
inside of this folder: [FONT=courier new]~/.thunderbird/*[random]*.default/extensions/cairo-dock-unread-messages@glxdock.org/chrome/[/FONT]
there was a outdated [FONT=Courier New]cairounread.js[/FONT] file, i have attached the updated working copy of this file i found on my laptop

---

