---
title: "Package Manger will not run"
date: 2007-06-07
forum: General Help
---

### Post by kb7qqq on 2007-06-07
When I try to run the package manger I get the following error.

E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Also, could someone tell me how to edit the sources.list

Thanks
Sam

[email]kb7qqq@gmail.com[/email]

---

### Post by NeoLithium on 2007-06-07
It looks like there's something on line 44 of your /etc/apt/sources.list that is in front of the repository line.  Open it up ```
gksu gedit /etc/apt/sources.list
``` and scroll down. The lines should either start with deb or be commented out (have a # in front of them.)

If you can't find something weird, you can always copy and paste it here and we can help too :)

---

