---
title: "Can't upgrade to 18 version: 'NoneType' object has no attribute 'ver_str'"
date: 2019-04-22
forum: General Help
---

### Post by marcelo20 on 2019-04-22
Hi, I cannot upgrade to 18 Ubuntu Studio version. This is what happens when I try 'do-release-upgrade' on Terminal:
'NoneType' object has no attribute 'ver_str'

How to solve it?
Thank you

---

### Post by cruzer001 on 2019-04-23
Sounds like a PPA (third party software) is still installed on your system and there is no upgrade option.  If this is so, that package needs to be either removed or disabled.

Does it not say what package is hanging up the process?  That info should be just above the 'NoneType' entry.

---

