---
title: "Synaptic Package Manager Error"
date: 2013-06-21
forum: General Help
---

### Post by mtmoe on 2013-06-21
When I open Synaptic Package Manager, I get the following errror message:

E: Type 'ppa:ubuntu-wine/ppa' is not known on line 1 in source list /etc/apt/sources.list.d/additional-repositories.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any help resolving this issue would be appreciated!

---

### Post by plucky on 2013-06-21
Please post output from a terminal for ```
cat /etc/apt/sources.list.d/additional-repositories.list
```

Have you been trying to add additional repositories?

---

### Post by mtmoe on 2013-06-21
Output is ppa:ubuntu-wine/ppa

I was trying to get the wine repositories and this error showed right afterwards.

---

### Post by HiImTye on 2013-06-22
how did you try adding the repository?
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by mtmoe on 2013-06-22
Through the package manager.

---

### Post by 3rdalbum on 2013-06-22
```
sudo rm /etc/apt/sources.list.d/additional-repositories.list
sudo apt-get update
```

Try the instructions to add the PPA again, but this time follow a little more carefully.

---

### Post by mtmoe on 2013-06-23
Thanks for the help!

---

