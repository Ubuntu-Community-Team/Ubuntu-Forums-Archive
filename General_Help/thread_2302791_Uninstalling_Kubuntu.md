---
title: "Uninstalling Kubuntu"
date: 2015-11-13
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-13
I installed Kubuntu and manually uninstalled it using Synaptic Package Manager because I couldn't find it on Ubuntu Software Center.  Now when logging on for the past four days I get the below error.  Does anyone know what happened and how to get rid of the error?  The error pops up three times after clicking "cancel".

Damn, forgot to upload the image!  Here it is!

---

### Post by egeezer on 2015-11-13
For the error message: click the Report Problem button and wait while the report box loads, then look it over - it will tell you what the problem is, and you can send a bug report or look up from the reference just what the bug is all about.     For the uninstall, you probably need to purge kubuntu-desktop: ```
sudo apt-get remove --purge kubuntu-desktop
```

---

### Post by shane_faulkinbury2 on 2015-11-14
Thanks!  I did the purge and it went though a long list of things and then it said I should do an autoremove.  When I did it I got this.

---

