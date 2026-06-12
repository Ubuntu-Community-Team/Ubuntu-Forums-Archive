---
title: "new firefox 57.0 i cant open Skype"
date: 2017-11-10
forum: General Help
---

### Post by eagleftvp-co on 2017-11-10
Hi 
After the last update firefox to firefox  Quantum 57.0 (ubuntu 16.04) i Can open the skype..how to fix this??

---

### Post by walts48 on 2017-11-10
AFAIK Firefox 57.0 isn't going to be released until next week. Are you on the Beta update channel?

Check about:support.

Sorry I don't Skype, but am posting with 57.0rc2 from Mozilla. Mozilla/5.0 (X11; Linux x86_64; rv:57.0) Gecko/20100101 Firefox/57.0 ID:20171109183137

---

### Post by eagleftvp-co on 2017-11-11
Hi Thakns 
igot 57 from software update...yesterday...i run ubuntu 16.04 lts xenia , not yet 17 ubuntu..

---

### Post by litlesam on 2017-11-11
Been running 16.04 and 17.10 on a few different computers and all Firefox versions are still 56.x.x

---

### Post by kostkon on 2017-11-11
> **eagleftvp-co said:**
> Hi Thakns 
igot 57 from software update...yesterday...i run ubuntu 16.04 lts xenia , not yet 17 ubuntu..
Maybe you have enabled the Proposed repository or have added one of the mozilla team ppas. What's the output of the following command?:
```
apt-cache policy firefox
```

---

### Post by eagleftvp-co on 2017-11-11
eagle@eagle:~$ apt-cache policy firefox
firefox:
  Installed: 57.0+build1-0ubuntu0.16.04.1
  Candidate: 57.0+build1-0ubuntu0.16.04.1
  Version table:
 *** 57.0+build1-0ubuntu0.16.04.1 500
        500 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status
     56.0+build6-0ubuntu0.16.04.2 500
        500 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
     45.0.2+build1-0ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        500 [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
eagle@eagle:~$

---

