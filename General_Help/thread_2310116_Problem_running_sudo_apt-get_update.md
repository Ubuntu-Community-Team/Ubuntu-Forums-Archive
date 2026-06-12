---
title: "Problem running sudo apt-get update"
date: 2016-01-16
forum: General Help
---

### Post by satimis on 2016-01-16
Hi all,

Ubuntu 14.04 desktop

Problem running sudo apt-get update```

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have been searching a while on Internet and found following suggestion;```

sudo rm /var/lib/apt/lists/* -vf

```

But problem still remains.  Please help.  Thanks

satimis

---

### Post by blueridgedog on 2016-01-16
Try 

```
sudo rm /var/lib/apt/lists/* -vfr
sudo apt-get clean; sudo apt-get update
```

---

### Post by satimis on 2016-01-16
> **blueridgedog said:**
> Try 

```
sudo rm /var/lib/apt/lists/* -vfr
sudo apt-get clean; sudo apt-get update
```

Thanks for your advice.  Problem remains

sudo rm /var/lib/apt/lists/* -vfr
sudo apt-get clean; sudo apt-get update```

.....
.....
Fetched 32.4 MB in 11s (2,922 kB/s)                                            
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

satimis

---

### Post by blueridgedog on 2016-01-16
It could be that the error is legit.  Te hash you are calculating is off either due to a file corruption issue at the source or a memory error on your end resulting in a bad hash (not likely).  Baring any other information I would concluded that the host site has an issue for now, but it is hard to escape the fact that is could be a local issue.

---

### Post by XBNCPRk on 2016-01-17
Does the error still exist if you switch to another mirror?

---

### Post by satimis on 2016-01-17
> **XBNCPRk said:**
> Does the error still exist if you switch to another mirror?
Hi,

Original source.list

```

deb http://hk.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

deb http://hk.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty universe
deb http://hk.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty-updates universe

deb http://hk.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

Changed to Singapore mirror

```

deb http://sg.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty main restricted

deb http://sg.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

deb http://sg.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty universe
deb http://sg.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty-updates universe

deb http://sg.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://sg.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

deb http://sg.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://sg.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

Problem still remains```

.....
W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

This error just happened recently.  It didn't happen before.

Regards
satimis

---

### Post by satimis on 2016-01-19
Hi all,

Further to my late posting;

If comment out following repo on source.list```

#deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
#deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

#deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-updates universe
#deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-updates universe

#deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
#deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

```
all errors gone.

Regards
satimis

---

