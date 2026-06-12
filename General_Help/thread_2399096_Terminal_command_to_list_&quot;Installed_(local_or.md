---
title: "Terminal command to list &quot;Installed (local or obsolete)&quot; packages?"
date: 2018-08-21
forum: General Help
---

### Post by &amp;KyT$0P# on 2018-08-21
In Synaptic Package Manager, there is an option to list the packages that are "Installed (local or obsolete)".  What is the terminal command to get this same list?

(I tried [FONT=Courier New]aptitude search '(?obsolete)'[/FONT] but it doesn't list the locally-installed packages for which an older version is available in the standard repositories.)

---

### Post by TheFu on 2018-08-21
$ sudo ubuntu-support-status ... something something something.

---

### Post by &amp;KyT$0P# on 2018-08-21
Thanks TheFu!

This command comes close -
```
ubuntu-support-status --show-unsupported
```
It gives exactly the list of packages I want, but surrounded by a bunch of other info that I don't want.  Looking at the [FONT=Courier New]ubuntu-support-status[/FONT] script shows how to write my own Python 3 script to print only the desired info, so I'll do that for now.

(And just to add, because Internet searching didn't find any documentation of the [FONT=Courier New]apt[/FONT] Python 3 module: said documentation can be installed by running [FONT=Courier New]sudo apt-get install python-apt-doc[/FONT] )

---

### Post by &amp;KyT$0P# on 2018-08-23
Here's the Python 3 script I ended up with.  I named it [FONT=Courier New]apt-locally-installed[/FONT]
```
#!/usr/bin/env python3

import apt

with apt.Cache() as cache:
  for pkg in cache:
    if pkg.is_installed and not(pkg.candidate and pkg.candidate.downloadable):
      print(pkg.name, pkg.installed.version, sep='\t')

```

---

