---
title: "trouble installing libtiff4-dev"
date: 2005-07-23
forum: General Help
---

### Post by caratcus on 2005-07-23
I initially asked this elsewhere, but realized that the other was the wrong forum.  Here goes again.

I am trying to install hugin based on the instructions [here](http://rbpark.ath.cx/articles/compile-hugin-ubuntu) but ran into a problem with libtiff4-dev:

```
caratcus@Linux:~$ apt-cache search libtiff4
libtiff4-dev - Tag Image File Format library, development files
libtiff4 - Tag Image File Format library
```

followed by:```

caratcus@Linux:~$ sudo apt-get install libtiff4-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libtiff4-dev: Depends: libtiff4 (= 3.6.1-5) but 3.6.1-5ubuntu0.1 is to be installed
E: Broken packages
```

The link I initially gave includes another link to [the ubuntu 5.04 Starter Guide](http://ubuntuguide.org/#extrarepositories) which gives directions I followed to add repositories.

Have I done something wrong?  Is there some way to force installation that I've not yet seen?  I've been trying to figure this out off and on for a month or so now, and am getting a little tired of getting nowhere.  ideas?  please?

Sorry if this is easy to solve, but I'm quite new to Debian-based distros.

Thanks.

-caratcus

---

