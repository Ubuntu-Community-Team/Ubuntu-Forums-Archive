---
title: "Compiling NetworkManager"
date: 2005-10-05
forum: General Help
---

### Post by akseli on 2005-10-05
Hey, I've found various threads on this topic but none of them seem to relate to my exact problem so I just decided to post another thread ... never hurt anyone, right?

Anyhow, I went through all the darn dependencies as well as I could using Synaptics (running Hoary with all updates) and the ./configure goes perfectly, it ends by saying that it's been configured for debian... fine by me ... but then the compiler fails with some error about dbus not having declared a variable or something of the sort. If anyone is interested in helping please ask for the exact error and I'll paste here for you.

Thank you!

---

### Post by mlomker on 2005-10-05
You can't run it on Hoary but there are pre-built packages for Breezy floating around.  NetworkManager requires a newer version of libc6 than Hoary has and you can't upgrade libc6 because most of the system is build against the installed version (you *could* seriously break your system trying...ask me how I know).  ;)

---

### Post by akseli on 2005-10-10
[QUOTE=mlomker]You can't run it on Hoary but there are pre-built packages for Breezy floating around.  NetworkManager requires a newer version of libc6 than Hoary has and you can't upgrade libc6 because most of the system is build against the installed version (you *could* seriously break your system trying...ask me how I know).  ;)[/QUOTE]

Thanks for your help! I actually decided to upgrade to Breezy and installed the packages from synaptic and evreything works like a wonder.
Can't wait to see if there are any last minute changes in Ubuntu when the final release of Breezy comes out.

Thanks again!

---

