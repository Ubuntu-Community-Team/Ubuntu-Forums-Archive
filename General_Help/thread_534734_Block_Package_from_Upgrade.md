---
title: "Block Package from Upgrade?"
date: 2007-08-25
forum: General Help
---

### Post by derouge on 2007-08-25
Is it possible to block one specific package from being upgraded? I have a program that only runs with an older version of Wine. This is also the only program I use Wine for, so I do not even need the newest version. Every time I apt-get update and upgrade the old version of Wine is overwritten by the newest one in the repos. Can I block this single upgrade from happening?

---

### Post by pizzutz on 2007-08-25
I haven't tried it, but according to the documentation I just looked up you would create the file /etc/apt/preferences  and put in something like this

```

Package: wine
Pin: version 0.9.37 (or whatever version)
Pin-Priority: 1001

```

see 
```

man apt-get

```

and

```

man apt_preferences

```

for more details.  I don't know for sure how to do what you are asking,  I just looked it up.

---

### Post by derouge on 2007-08-25
Okay, I'll look into that. I tried locking it in Synaptic and that didn't work. Thanks. :)

---

### Post by bapoumba on 2007-08-25
In Synaptic, highlight a package > Package > Lock version.

---

### Post by CptFuzzy on 2008-02-26
I tried locking a package in Synaptec, but that only locks it in Synaptec; the system update notifications still come up and apt still tries to update it.  There must be a global way of blocking a package... 

I tried the /etc/preferences fix, but that doesn't seem to work:

/etc/apt/preferences:
Package: language-pack-kde-en-base
Pin: 1:7.10+20071012
Pin-Priority: 1001

Package: language-pack-kde-en
Pin: 1:7.10+20071120
Pin-Priority: 1001


  aptitude  safe-upgrade:

The following packages will be upgraded:
  language-pack-kde-en [1:7.10+20071120 -> 1:7.10+20080205] language-pack-kde-en-base [1:7.10+20071012 -> 1:7.10+20080205]

---

### Post by Seisen on 2008-02-26
Check this out: [http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

---

### Post by CptFuzzy on 2008-02-26
> **Seisen said:**
> Check this out: [http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

This seems to only let you set priorities to repositories (Stable/Unstable/testing), not individual packages.  or am I missing something?

---

### Post by cyberdork33 on 2008-02-26
try 'aptitude hold'
> aptitude hold pkgname: Fix a package at its current version and don't upgrade it automatically (formerly an obscure echo-to-file command). unhold to remove the hold.

---

