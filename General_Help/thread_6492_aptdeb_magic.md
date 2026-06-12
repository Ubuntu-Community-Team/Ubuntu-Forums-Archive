---
title: "apt/deb magic"
date: 2004-11-29
forum: General Help
---

### Post by boobis on 2004-11-29
In my quest to fix ACPI for my laptop I am now forced to reinstall the entire /etc/acpi directory. And it hits me that I dont know how to do it...

How do I find out from which deb-package a specific file comes? which tool do I use?

I have tried the man-pages for apt-cache, aptitude, dep and whatnot, but I can't find out how to do it.

Regards
/joel

---

### Post by WW on 2004-11-29
**dpkg**  provides another powerful set of incantations for practicing apt/deb magic :)

To find which package installs <filename>, use the command ```
dpkg -S <filename>
```

---

### Post by boobis on 2004-11-30
Thanx mate! That solved the problem, and got me on track with the real issues :D

/joel

---

