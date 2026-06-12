---
title: "Can I get a list of packages I installed?"
date: 2021-04-06
forum: General Help
---

### Post by sofasurfer on 2021-04-06
I know how to get a list of packages installed in my system. That is a list of all packages in the system. Is there a way to get a list of packages that _I personally installed_ without having to dig through a whole list of thousands of packages that came with the system install?

---

### Post by CatKiller on 2021-04-06
Getting a list of packages is easy.

Getting a list of installed packages is easy. 

When you install a package yourself, it is marked as "manually installed;" dependencies that are brought in as a result are marked as "automatically installed." Getting a list of manually-installed packages is easy.

As part of the installation process, some packages are marked as manually installed, even though it was the installer that did it. Getting a list of these packages, so you can exclude them, from the manifest file is fiddly, but doable, as I understand it.

How complicated the whole thing ends up depends on how far down the rabbit hole you want to go. There are tools, scripts, and commands to tackle all of these bits, some of them already posted here on the forum.

---

### Post by sofasurfer on 2021-04-06
> **CatKiller said:**
> Getting a list of packages is easy.

When you install a package yourself, it is marked as "manually installed;" dependencies that are brought in as a result are marked as "automatically installed." Getting a list of manually-installed packages is easy.

As part of the installation process, some packages are marked as manually installed, even though it was the installer that did it. Getting a list of these packages, so you can exclude them, from the manifest file is fiddly, but doable, as I understand it.


This is what I suspected but was unsure because of the packages the installer installed and marked as "manual".
I see now that the "manual" installed package list lists only 40 total so its easy to weed out the few that I did not install myself. So I got my answer. Thanks.

---

### Post by ActionParsnip on 2021-04-06
Please remember to mark as solved if the issue is sorted

---

### Post by cmcanulty on 2021-04-06
Or go to synaptic-file-save markings as and check the bottom left box that says save full state and then you have your settings also. I save that list weekly. It takes <1 second to run. The manually installed may be missed though. Make it a part of your normal backups. You can save it wherever you want, it is a simple text file.

---

