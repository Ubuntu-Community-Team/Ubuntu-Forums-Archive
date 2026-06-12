---
title: "About packages G++ and G++-5 or G++-6"
date: 2017-08-06
forum: General Help
---

### Post by satimis on 2017-08-06
Hi all

Ubuntu 16.04 desktop 

I need to install following packages

G++
and
G++-5 or G++-6

&#10219; apt-cache policy build-essential```

build-essential:
  Installed: 12.1ubuntu2
  Candidate: 12.1ubuntu2
  Version table:
 *** 12.1ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

&#10219; apt-cache policy git```

git:
  Installed: (none)
  Candidate: 1:2.7.4-0ubuntu1.1
  Version table:
     1:2.7.4-0ubuntu1.1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1:2.7.4-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

&#10219; apt-cache policy g++```

g++:
  Installed: 4:5.3.1-1ubuntu1
  Candidate: 4:5.3.1-1ubuntu1
  Version table:
 *** 4:5.3.1-1ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

What other packages I need to install?  Thanks

Regards
satimis

---

### Post by steeldriver on 2017-08-07
Need to install why?

`g++` is just a dependency package that points to the current version of the 'real' g++ package for your system (which is 5.3.1 on Xenial)

So you have g++-5

All should be good - what actual issue are you trying to resolve?

---

### Post by satimis on 2017-08-07
> **steeldriver said:**
> Need to install why?

`g++` is just a dependency package that points to the current version of the 'real' g++ package for your system (which is 5.3.1 on Xenial)

So you have g++-5

All should be good - what actual issue are you trying to resolve?
Hi,

I'm now testing;

ViewTouch
[https://github.com/ViewTouch/viewtouch/wiki/Building](https://github.com/ViewTouch/viewtouch/wiki/Building)

on Ubuntu16.04 desktop

it needs to install:-
G++
G++-5 or G++-6
xfonts-50dpi
etc.

I can't find xfonts-50dpi on repo.  xfonts-100dpi is available

Regards
satimis

---

### Post by steeldriver on 2017-08-07
Did you actually try building it without that? The [ViewTouch wiki](https://github.com/ViewTouch/viewtouch/wiki) says

> ViewTouch makes use of the bitmapped X11 100 dpi fonts which are found in the xfonts-base package.

You may find that it works fine without xfonts-50dpi (or they may only be required for certain legacy display resolutions).

---

### Post by satimis on 2017-08-07
> **steeldriver said:**
> Did you actually try building it without that? The [ViewTouch wiki](https://github.com/ViewTouch/viewtouch/wiki) says



You may find that it works fine without xfonts-50dpi (or they may only be required for certain legacy display resolutions).

Thanks

I'll test it.

Regards
satimi

---

