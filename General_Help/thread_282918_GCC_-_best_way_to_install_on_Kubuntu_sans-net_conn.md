---
title: "GCC - best way to install on Kubuntu sans-net connection?"
date: 2006-10-23
forum: General Help
---

### Post by ehird on 2006-10-23
After many years of trying Linux, Kubuntu installs easily, and it works! Great! :D

However, I have a bit of a problem.

My modem is the scourge of the devil - SAGEM F@ST 800. It never works on Linux - until today, I found updated linux drivers on their site! Unfortunately, it's source code and a patch. The patch seemed to be already compiled, so I ./configure'd. It says it couldn't find GCC, so I checked and - yep, not there. So I need a way, without a net connection (i can download things on this winxp install, however, and burn them to a disk/put them on a linux-accessible HD), that includes automake (I think I'd need this?) etc.

What's a good, user friendly way to get that?

Thanks for any help in advance, you guys are great. :)

---

### Post by skymt on 2006-10-23
There is no user-friendly way to do it. However, you can download the packages you need (m4, automake, autoconf, gcc, etc) in .deb, directly from the [archive](http://archive.ubuntu.com/ubuntu/pool/main/). You'll want at least the packages required by [build-essential](http://packages.ubuntu.com/dapper/devel/build-essential), plus whatever libraries (and associated -dev packages) the drivers need.

EDIT: Note that the archive has all versions of the packages mixed together. For each package you want to install, look up (on packages.ubuntu.com) the version of the package used in the version of Ubuntu you have installed.

---

### Post by ehird on 2006-10-23
Alright... would have thought someone would have anticipated this problem but will do it as a learning experience. :)

I'll report back to this thread.

---

