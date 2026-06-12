---
title: "[apt-get] ESSENTIAL beginner question!!"
date: 2008-05-24
forum: General Help
---

### Post by kakyoism on 2008-05-24
Whenever I try to remove a package,
I see this:
```
The following packages were automatically installed and are no longer required
```
```
Use 'apt-get autoremove' to remove them.
```
Should I do as it says to remove those libs as well?
Up till now I've been too scared to follow that...

Please give an idea!
Thx!

---

### Post by pointone on 2008-05-24
dpkg is smart--I've never had a problem caused by following its instructions.

What happened is that you installed a package that depended on several other packages, which were automatically installed to satisfy the dependencies. After removing the manually installed package, the automatically installed ones were not automatically removed, and are no longer required.

Short answer: run "sudo apt-get autoremove".

---

