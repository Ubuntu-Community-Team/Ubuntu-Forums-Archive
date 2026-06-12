---
title: "Trouble with dependancies for libc6"
date: 2012-10-21
forum: General Help
---

### Post by scottgutman on 2012-10-21
Hello,

I would like to install libc6-dev to my machine but I am getting a dependency issue. Here is what I did. I am logged in as root, so sudo is not an issue.

1. I ran the update: **apt-get update**
2. I ran **apt-get -f install libc6-dev** and got this error:
```
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.11.1-0ubuntu7.10 is to be installed
E: Broken packages

```
3. I tried **apt-get install libc6-dev=2.11.1-0ubuntu7.8** to force the matching version and got the same error as before.
4. I looked in the libc6 package **dpkg -s libc6**, and below is part of the output. Notice the version number **2.11.1-0ubuntu7.10** and is not what is reported by apt-get.  
```
Version: 2.11.1-0ubuntu7.10
Replaces: belocs-locales-bin
Provides: glibc-2.10-1
Depends: libc-bin (= 2.11.1-0ubuntu7.10), debconf (>= 0.5) | debconf-2.0, libgcc1, tzdata, findutils (>= 4.4.0-2ubuntu2)
```

I am not sure how to proceed. Can you help me fix this and get libc6-dev installed?

My system is running Zentyal 2.2 | Ubuntu 10.04.4 LTS | Linux 2.6.32-42-server #95-Ubuntu x86_64

---

### Post by mc4man on 2012-10-21
Check in your software sources that under the 'updates' tab both security & updates are enabled. Then update your sources & try again

This is the current version of libc6-dev in lucid
[http://packages.ubuntu.com/lucid/libc6-dev](http://packages.ubuntu.com/lucid/libc6-dev)

---

