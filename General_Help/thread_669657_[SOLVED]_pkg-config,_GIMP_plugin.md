---
title: "[SOLVED] pkg-config, GIMP plugin"
date: 2008-01-16
forum: General Help
---

### Post by niethslim on 2008-01-16
When compiling something, often when a dependency is not met it tells me to install it or if it is installed  to change the PKG_CONFIG_VARIABLE or alternatively change some other variables. 
When this happens I usually just install the dependency.
Now, I'm trying to install a plugin for gimp that requires the package 'gimp-2.0', I have gimp 2.4.3 installed with the package name 'gimp'.
But although gimp is installed I can't find no .pc file for it.

What should I do?

Thanks,

---

### Post by geirha on 2008-01-16
pkg-config files are installed by packages ending with -dev. In this case It's most likely libgimp2.0-dev you want installed.

---

### Post by niethslim on 2008-01-16
Thanks, that worked.

---

### Post by geirha on 2008-01-16
Good to hear, could you mark it as [solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)? Makes it easier for people with a similar problem to find a solution.

---

