---
title: "opensync-plugin-sunbird"
date: 2008-05-31
forum: General Help
---

### Post by AbsolutIggy on 2008-05-31
Hello,

On 7.10 I used OpenSync witht he opensync-plugin-sunbird package to sync my Thunderbird Calendar (.ics file) with my mobile phone. Now with 8.04, I can't find the package anymore - it doesn't seem to exist for hardy. (not in package search or synaptic). I tried downloading the version for edgy from the package search page, but then it complains "Error: Dependency is not satisfiable: libneon25"

I can't download libneon25 from synaptic either. (I have libneon27 installed though..)

Does anybody know how I can get the proper plugin for syncing an .ics file using opensync? Either the sunbird one, or an alternative?

---

### Post by allspiritseve on 2008-07-29
I found a deb for libneon25 here: [http://packages.debian.org/etch/libneon25](http://packages.debian.org/etch/libneon25)... and then I could install libopensync-plugin-sunbird just fine. 

However, once that was up and running, I get this:

```
Error while initializing syncengine: (null)
```

I think it might have something to do with the fact that Sunbird/Lightning now uses SQLite for its backend, instead of ICS files. Does anyone know how to use opensync with sql databases?

---

### Post by AbsolutIggy on 2008-07-30
I've installed libneon25 somehow (forgot how.. may have been from an old repository).

I don't sync with a SQLite database, but with .ics files. In lightning I use a "network calendar" located at file:///home etc...

This works fine, just have to remember to "reload the remote calendar" in lightning once I've synced, to see the changes.

---

