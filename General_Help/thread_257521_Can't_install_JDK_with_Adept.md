---
title: "Can't install JDK with Adept"
date: 2006-09-14
forum: General Help
---

### Post by PigCorpse on 2006-09-14
Hi!

First post here. I'm using Kubuntu and I want to install JDK using Adept.

After download it, it begins installing. It stops when it gets to the real JDK package and I was wonderign why. I clicked 'Show Details' and I found that there was a Terminal-like blue screen with one of those dialogs that ask if I accept the license agreement or not. It has an 'OK' option, but I can't select it. I tried pressing enter with my keyboard and clicking with the mouse, it doesn't work.

Any help?

Thanks!

---

### Post by lamego on 2006-09-14
Maybe its a better option to install it from the terminal:
```
sudo apt-get install package_name
```

---

### Post by PigCorpse on 2006-09-14
Wow, thanks for the quick response. I'll try that in a few minutes.

What is the difference between using the terminal and using a package manager?

And can you tell me other commands for downloading things? I know of this other one 'wget' but I don't know their differences.

From what I uneducatedly guess:

sudo (to have root privilages) apt-get ('get' seems to mean download, and APT is the tool for packages, so you're downloading from the packages) install (means to install) and the package name. Is that correct?

---

