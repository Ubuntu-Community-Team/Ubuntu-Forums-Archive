---
title: "apt-get / md5sum problem with libexpat1"
date: 2005-07-13
forum: General Help
---

### Post by capehart on 2005-07-13
I've just done a server install of Hoary, and am new to the Ubuntu/deb world. I was attempting to install apache2 and php via apt-get or aptitude (no desktop, ergo no synaptic).

Apt-get fails in the retreival of a couple of the dependency packages. As a specific example, it fails with libexpat1_1.95.8-1_i386. (also libkrb and libmysqlclient). At least, those are the items that show up in /var/cache/apt/archives/partial/

The specific transaction goes as follows:

**root@store1:/home/capehart #** *apt-get install libexpat1*
```

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libexpat1
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 59.4kB of archives.
After unpacking 188kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hoary/main libexpat1 1.95.8-1 [59.4kB]
Fetched 59.4kB in 0s (67.6kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_1.95.8-1_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I've run **apt-get update**.

I can confirm that the md5 sum listed in *apt-cache show libexpat1* (d112558a94e51bc213d3f1bbe63fc64d) is different from the md5sum that I compute on /var/cache/apt/archives/partial/libexpat1_1.95.8-1_i386.deb.FAILED (654aeea0f241afe7375c10800127e7c3). However, even downloading libexpat1 from us.archive.ubuntu.com to another machine results in the same md5sum as the one in /var/cache/apt/archives/partial, so I'm fairly confident that I don't have a corrupted download.

On the advice of a friend who's used .deb's longer than I have, I tried installing with the *--allow-unauthenticated* flag, but still get the same error: MD5Sum mismatch E: Unable to fetch some archives, maybe run apt-get update...

I must not be the only person trying to install apache and therefore libexpat1, but I haven't found other references in this forum.  

Can anyone offer some guidence please?

TIA,
AC

---

### Post by Leif on 2005-07-13
The us repos are having problems, switch another country, such as nl.

---

### Post by capehart on 2005-07-13
Worked like a charm. Thank you!

---

