---
title: "Broken dependencies in libnss3-1d"
date: 2014-04-07
forum: General Help
---

### Post by Rehd on 2014-04-07
Hi,

prefixed "Xubuntu", since that is what I am running, but I think the problem is not specific. The library libnss3-1d depends on a newer version of libnss3, but the latter is up to date according to aptitude. How do I resolve this paradox?


My system is Xubuntu 13.10-saucy AMD64. Following the uname -a output:

```
3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```


I cannot say how and when this happened, just the other day on my production machine and I am/was very busy and could not focus on it. I did nothing special but safe-upgrade and install from repos.

Suddenly

```
sudo aptitude safe-upgrade
```

complaines about broken dependencies and

```
sudo aptitude safe-upgrade --full-resolver
```

produces the following broken package:

```
libnss3-1d : Depends: libnss3 (= 2:3.15.4-0ubuntu0.13.10.2) but 2:3.15.4-0ubuntu0.13.10.1 is installed.
```

Although
```
aptitude show libnss3
```
gives

```

rforge@xbk:~$ aptitude show libnss3
Package: libnss3                         
State: installed
Automatically installed: no
Multi-Arch: same
Version: 2:3.15.4-0ubuntu0.13.10.1
Priority: optional
Section: libs
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 3,702 k
Depends: libc6 (>= 2.14), libnspr4 (>= 2:4.9-2~) | libnspr4-0d (>= 4.8.6), libsqlite3-0 (>= 3.5.9), zlib1g (>= 1:1.1.4)
PreDepends: multiarch-support
Conflicts: libnss3-1d (< 2:3.13.4-2), libnss3-1d (< 2:3.13.4-2)
Breaks: libnss3 (!= 2:3.15.4-0ubuntu0.13.10.1)
Replaces: libnss3 (< 2:3.15.4-0ubuntu0.13.10.1)

```

What am I missing and what can I do about this?

Any help appreciated,
best regards,
Reinhard

---

### Post by mc4man on 2014-04-07
libnss3-1d (2:3.15.4-0ubuntu0.13.10.2) is a security update for saucy & as seen deps on libnss3 (2:3.15.4-0ubuntu0.13.10.2 (saucy-updates
So check & make sure in "Software & Updates" that both are enabled under the Updates tab. If they already are or you needed to enable then update your sources & recheck.
```
apt-cache policy libnss3 
```
should show  2:3.15.4-0ubuntu0.13.10.2  as either being installed or available. If not then maybe switch server if using a mirror to another server or to the Main server, update sources & recheck with apt-cache

---

### Post by Rehd on 2014-04-08
Thank you so much mc4man, you guys are doing a great job and it is very much appreciated.

Stupid me did indeed uncheck "Security Updates" in "Software&Updates". I rechecked them and voila, everything fine.

THX.

---

