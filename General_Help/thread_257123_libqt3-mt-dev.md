---
title: "libqt3-mt-dev"
date: 2006-09-14
forum: General Help
---

### Post by Bosambo on 2006-09-14
I'm trying to install moto4lin and it seems I have to use the command qmake to do this.
I ran a search and found a tutorial on [installing moto4lin]("http://www.ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin") but on the line where I enter 

```
~$sudo apt-get install libqt3-mt-dev 

```
into the terminal I get

```
tes@tes-desktop:~$ sudo apt-get install libqt3-mt-dev
Reading package lists... Done
Building dependency tree... Done
Package libqt3-mt-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  qt3-qtconfig qt3-linguist qt3-dev-tools-embedded qt3-dev-tools-compat
  qt3-designer qt3-assistant
E: Package libqt3-mt-dev has no installation candidate
```

Anyone have any idea where I'm going wrong? Total linux spaz by the way so be gentle with me. 

Thanks all.

---

### Post by Ramses de Norre on 2006-09-14
What are your sources? Do you have all repos enabled?
I've got the package available here, It's in the main repo.

---

### Post by Bosambo on 2006-09-14
Found the solution **[here]("http://ubuntuforums.org/showthread.php?t=227117")**...something to do with dependencies

---

