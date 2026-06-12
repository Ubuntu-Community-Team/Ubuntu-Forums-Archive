---
title: "Opera Browser"
date: 2023-03-14
forum: General Help
---

### Post by speartip on 2023-03-14
I know that this has been an issue for a while now, but has anyone managed to get Opera to play mp4 files? And if so, how? I've tried a number of "fixes" online to no avail.
Also, as I'm using the official .deb package from Opera's website, does the snap version from the repos work any better?

---

### Post by ActionParsnip on 2023-03-14
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy `dpkg -l | grep ^ii | grep -i opera | awk {'print $2'}`

```

---

### Post by speartip on 2023-03-14
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy
Linux wayne-Aspire-TC-885 5.19.0-35-generic #36~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb 17 15:17:25 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
eject:
  Installed: 2.37.2-4ubuntu3
  Candidate: 2.37.2-4ubuntu3
  Version table:
 *** 2.37.2-4ubuntu3 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
gpg:
  Installed: 2.2.27-3ubuntu2.1
  Candidate: 2.2.27-3ubuntu2.1
  Version table:
 *** 2.2.27-3ubuntu2.1 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy-updates/main amd64 Packages
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.2.27-3ubuntu2 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main amd64 Packages
libboost-filesystem1.74.0:
  Installed: 1.74.0-14ubuntu3
  Candidate: 1.74.0-14ubuntu3
  Version table:
 *** 1.74.0-14ubuntu3 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
opera-stable:
  Installed: 96.0.4693.50
  Candidate: 96.0.4693.50
  Version table:
 *** 96.0.4693.50 500
        500 https://deb.opera.com/opera-stable stable/non-free amd64 Packages
        100 /var/lib/dpkg/status
python3-macaroonbakery:
  Installed: 1.3.1-2ubuntu0.1
  Candidate: 1.3.1-2ubuntu0.1
  Version table:
 *** 1.3.1-2ubuntu0.1 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy-updates/main amd64 Packages
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1.3.1-2 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main amd64 Packages
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main i386 Packages
python3-more-itertools:
  Installed: 8.10.0-2
  Candidate: 8.10.0-2
  Version table:
 *** 8.10.0-2 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main amd64 Packages
        500 http://mirror.sov.uk.goscomb.net/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
```

---

