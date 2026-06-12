---
title: "Can Not Check &quot;Source Code&quot; in Software Updates"
date: 2020-03-11
forum: General Help
---

### Post by Rick St. George on 2020-03-11
Sorry Guys ... couldn't find an answer to this one!

A friends machine running Xubuntu v18.04, in Repositories / Software Updates / Ubuntu Software / 
"source code" will not allow to Check-it. Found this out when attempting to install Opera in Synaptic Pkg. Mgr. and Opera didn't show up.

All the others are checked!!!
Why would it now allow to CHECK or SELECT Source Code ???

Anyone have a clue? I'm pretty sure (I'll know on my next visit) he is signed on as Admin. If not, and we don't know the Admin PW, perhaps I could start Synaptic Pkg. Mgr. with sudo!??! Never tried that.

---

### Post by webaake on 2020-03-12
Hmm, strange. But you could add src repos manually to /etc/apt/sources.list like so; ```
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) bionic-security universe restricted multiverse main #Added by software-properties
```

Note the start with "deb-src" and "bionic" for 18.04.

By the way, the best way to open Synaptic with admin permissions is from the terminal with ```
pkexec synaptic
```

Many years it was with gksudo but that functonailty disappeared some time ago. 

PS: ditch "Software Center", it seems to lack functionality but it has a nice looking GUI!

---

