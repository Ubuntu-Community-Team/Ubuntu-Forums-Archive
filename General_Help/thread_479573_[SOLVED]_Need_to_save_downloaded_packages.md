---
title: "[SOLVED] Need to save downloaded packages"
date: 2007-06-20
forum: General Help
---

### Post by onegreenparker on 2007-06-20
I've been using Ubuntu 6.06 for about 8 months now and I'm very impressed, so I'm trying to get everyone I know onto the Ubuntu train.

However, one complaint I have is that once I install onto a new machine:
1) I will have to download the updates....again
2) I will have to download the various packages I have added....again

*Is there any way for me to save the packages I aleady have for installation on another machine*? I've used apt-get, Automatix2 and Add/Remove...so I don't know where the various packes are found.

---

### Post by dreadlord_chris on 2007-06-20
> **onegreenparker said:**
> I've been using Ubuntu 6.06 for about 8 months now and I'm very impressed, so I'm trying to get everyone I know onto the Ubuntu train.

However, one complaint I have is that once I install onto a new machine:
1) I will have to download the updates....again
2) I will have to download the various packages I have added....again

*Is there any way for me to save the packages I aleady have for installation on another machine*? I've used apt-get, Automatix2 and Add/Remove...so I don't know where the various packes are found.

Yup - it's called AptOnCD:
Description: CD-based repository creator for packages downloaded via APT
 Tool for the creation of a CD-based repository containing all packages
 downloaded via apt-get. Helpful for a post-installation on several
 machines or a simple backup method to re-install the system.
 After you've created the CD, you will be able to add it as a repository,
 as if it were an Ubuntu 'CD 2'. To run it, type "aptoncd" in a terminal.
 Or alternatively, via System -> Administration -> APTonCD menu entry.
 .
 For more information, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

```

sudo apt-get install aptoncd

```

---

### Post by onegreenparker on 2007-06-21
Worked like a charm..
However,
```

sudo apt-get install aptoncd

```
didn't work, I probably don't have the repo setup right.


But downloading source,
```

make

```
then 
```

sudo make install

```
did the trick.

---

