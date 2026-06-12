---
title: "Missing newline problem"
date: 2006-08-03
forum: General Help
---

### Post by jg_pm on 2006-08-03
I have a problem trying to repair a broken package and installing or upgrading packages, i get the error message in synaptic:

E: /var/cache/apt/archives/libxrandr2_6.8.2-10.2_i386.deb:  files list file for package `libksieve0' is missing final newline

This seems to have arisen after an attempt to upgrade from 5.04 to 5.10, i'm still running 5.04.

Any help would be greatly appreciated.

---

### Post by jg_pm on 2006-08-03
Fixed it with the help of a post from another thread:

[LIST]
[*]I moved the /var/lib/dpkg/info directory to a temporary directory
[*]Ran synaptic and re-installed the broken package
[*]removed libksieve0 in synaptic then re-installed it
[*]listed the files in the new /var/lib/dpkg/info directory
[*]deleted the corresponding files in the temporary directory (the old /var/lib/dpkg/info)
[*]moved the files from the new /var/lib/dpkg/info into the temporary directory
[*]removed /var/lib/dpkg/info
[*]renamed the temporary directory to /var/lib/dpkg/info
[/LIST]

---

