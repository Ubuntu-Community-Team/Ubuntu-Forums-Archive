---
title: "Cant Install Democracy Player - unmet dependencies"
date: 2007-05-26
forum: General Help
---

### Post by superyounan1 on 2007-05-26
```

sudo apt-get install democracyplayer


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  democracyplayer: Depends: python (< 2.5) but 2.5.1-0ubuntu3 is to be installed
                   Depends: mozilla-dev but it is not installable
                   Depends: mozilla-psm but it is not installable
E: Broken packages


```

I tired installing mozilla-dev and mozilla-psm separately without luck, and is there a way to get around having to downgrade python?

---

### Post by aug_aug on 2007-05-30
I've had the same issue. All I could find out was "wait until .9.6", or whatever the next version is.

---

### Post by H.E. Pennypacker on 2007-05-30
Democracy Player is available through Add/Remove.  It is also available through Automatix.

Edit:  You also need to fix your broken packages through Synaptic.

---

### Post by superyounan1 on 2007-05-30
> **H.E. Pennypacker said:**
> Democracy Player is available through Add/Remove.  It is also available through Automatix.

Edit:  You also need to fix your broken packages through Synaptic.

the verson of democracy avaliable through add/remove + automatix is very out dated, and doesnt seem to work right for me.

the newer version is much more sleek, i have it on windows, but it has a nasty mem leak issue there, was curious if it performs better in ubunutu

---

### Post by H.E. Pennypacker on 2007-05-31
> **superyounan1 said:**
> the verson of democracy avaliable through add/remove + automatix is very out dated, and doesnt seem to work right for me.

the newer version is much more sleek, i have it on windows, but it has a nasty mem leak issue there, was curious if it performs better in ubunutu

You could always download it from [http://www.getdeb.net/release.php?id=976](http://www.getdeb.net/release.php?id=976).  That's from GetDeb's website.  It has the latest version (I checked DP's official website to match the version).

---

### Post by superyounan1 on 2007-05-31
> **H.E. Pennypacker said:**
> You could always download it from [http://www.getdeb.net/release.php?id=976](http://www.getdeb.net/release.php?id=976).  That's from GetDeb's website.  It has the latest version (I checked DP's official website to match the version).

thanks! I didnt know about that site, excellent

---

