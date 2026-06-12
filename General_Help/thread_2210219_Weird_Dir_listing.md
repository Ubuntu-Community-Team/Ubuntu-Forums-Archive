---
title: "Weird Dir listing"
date: 2014-03-09
forum: General Help
---

### Post by garethinbendigo on 2014-03-09
Im building a website and Apache happily reads files in the themes dir, however I am unable to cd or list files in the themes dir from the command line.
When I do ls -la /var/www/project/themes the output is: d????????? ? ? ? ? ?          ? myproject
Has anyone seen that before and can let me in on what it means?

---

### Post by steeldriver on 2014-03-09
It probably means you don't have *execute* permission to the directory (the execute bit must be set in order to open a directory and read the contents)

---

