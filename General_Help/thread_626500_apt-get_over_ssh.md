---
title: "apt-get over ssh://"
date: 2007-11-29
forum: General Help
---

### Post by cbkm on 2007-11-29
Hi,

I'm trying to use an entry in my /etc/apt/sources.list like this:-

```

deb ssh://user@packages.example.com:/var/lib/packages/customer1 ./

```

I've setup the appropriate ssh keys so apt can access the server over ssh.

It seems to work ok, a brief check with apt-cache policy shows this:-

```

# apt-cache policy package
package:
  Installed: 0.09-1
  Candidate: 0.10-1
  Version table:
     0.10-1 0
        500 ssh://user@packages.example.com ./ Packages
 *** 0.09-1 0
        100 /var/lib/dpkg/status

```

But...When I try to install the package it does this:-

```

# apt-get install package
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  package
1 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
Need to get 8788B of archives.
After unpacking 8192B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  package
Install these packages without verification [y/N]? y
Errssh://user@packages.example.com ./ package 0.10-1
  File not found
Failed to fetch ssh://user@packages.example.com:/var/lib/packages/customer1//var/lib/packages/customer1/package_0.10-1_all.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I'm ok with the unauthenticated warning cause I haven't set that up yet, but I'm not sure how to fix the fact that it won't download it (obviously because it's adding the path twice).

Anyone have any ideas?

---

### Post by cbkm on 2007-11-29
Just solved this myself... (Seems like the post and solve works here as well as puzzledonkey :D)

The following sources.list line does the trick:-

```

deb ssh://user@packages.example.com /var/lib/packages/customer1/

```

---

