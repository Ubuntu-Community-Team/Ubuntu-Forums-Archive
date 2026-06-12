---
title: "repository authentication for archive and security repos?"
date: 2006-12-04
forum: General Help
---

### Post by imaiden22 on 2006-12-04
Hi everyone, Im having a problem with my repositories because the basic repos that are available out of the box with ubuntu seem to need authentication which they didn't need before before my current installation, and the same thing happens when I enable the universe and multiverse repositories.

Here is my output:

```
nick@nick-desktop:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:2 http://us.archive.ubuntu.com edgy Release [34.7kB]
Ign http://us.archive.ubuntu.com edgy Release
Get:3 http://us.archive.ubuntu.com edgy/universe Packages [3559kB]
Get:4 http://us.archive.ubuntu.com edgy/universe Sources [1068kB]              
Fetched 4662kB in 25s (184kB/s)                                                
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
```

---

### Post by yabbadabbadont on 2006-12-04
Try removing the "us." from the front of the entries in /etc/apt/sources.list so that you are using the main repositories instead of the US mirror.  The US mirror seems to have problems more often than others for some reason.

---

### Post by imaiden22 on 2006-12-04
I guess it didn't work:

```
Get:7 http://archive.ubuntu.com edgy/universe Packages [3559kB]
Get:8 http://archive.ubuntu.com edgy/universe Sources [1068kB]                 
Fetched 4697kB in 18s (258kB/s)                                                
Reading package lists... Done
W: GPG error: http://security.ubuntu.com edgy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
```

Thanks for the advice though, if you have any other ideas I'll give them a shot!

---

