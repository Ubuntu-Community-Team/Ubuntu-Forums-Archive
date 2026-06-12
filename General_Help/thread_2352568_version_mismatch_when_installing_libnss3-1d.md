---
title: "version mismatch when installing libnss3-1d"
date: 2017-02-13
forum: General Help
---

### Post by b_e_e_k on 2017-02-13
Hi -

I'm trying to install libnss3-1d. I run into this problem:

```

$ sudo apt-get install libnss3-1d
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libnss3-1d : Depends: libnss3 (= 2:3.15.4-1ubuntu7) but 2:3.17.1-0ubuntu0.14.04.2 is to be installed
E: Unable to correct problems, you have held broken packages.

```


I already have the newer version 2:3.17.1 of libnss3. However, it seems as if libnss3-1d only works with an older version of libnns3:

```

$ apt-cache policy libnss3
libnss3:
  Installed: 2:3.17.1-0ubuntu0.14.04.2
  Candidate: 2:3.17.1-0ubuntu0.14.04.2
  Version table:
 *** 2:3.17.1-0ubuntu0.14.04.2 0
        100 /var/lib/dpkg/status
     2:3.15.4-1ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

$ apt-cache policy libnss3-1d
libnss3-1d:
  Installed: (none)
  Candidate: 2:3.15.4-1ubuntu7
  Version table:
     2:3.15.4-1ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```


How should I go about installing libnss3-1d?
In case I have to revert to the older version of libnss3: What other dependencies may be broken? How to find out?

My Ubuntu version: 14.04 LTS
```

$ uname -a
Linux ... 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Background: This problem came about when working on the suggested solution to [https://ubuntuforums.org/showthread.php?t=2352462](https://ubuntuforums.org/showthread.php?t=2352462)

---

### Post by b_e_e_k on 2017-02-15
To resolve the dependency for libnss3-1d, I first had to revert back to older versions of two libnss3 packages, then install libnss3-1d:

```

sudo apt-get install libnss3=2:3.15.4-1ubuntu7 libnss3-nssdb=2:3.15.4-1ubuntu7
sudo apt-get install libnss3-1d

```


To see the versions of all libnss3-related packages:
```

sudo apt-cache policy libnss* 

```

A reverse depends shows all packages that depend on a given package:

```

apt-cache rdepends libnss3

```

---

