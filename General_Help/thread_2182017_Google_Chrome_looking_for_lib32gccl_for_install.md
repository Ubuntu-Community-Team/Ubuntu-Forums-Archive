---
title: "Google Chrome looking for lib32gccl for install"
date: 2013-10-19
forum: General Help
---

### Post by psfal on 2013-10-19
Installed Ubuntu 12.04 32bit on an older machine, tried to install Google Chrome and it states that a dependency is not met, it needs **lib32gccl**&#8203; to install. I tried installing it and was informed that there was no such package. Where do I get this?

---

### Post by Yellow Pasque on 2013-10-19
lib32gcc1 is available in the repo, but only for 64-bit installs. Most likely, you're trying to install a 64-bit Chrome package...

---

### Post by psfal on 2013-10-20
No, I downloaded the 32bit version of chrome, twice, this is the first time I've installed a 32bit version of Ubuntu on anything though

---

### Post by drmrgd on 2013-10-20
Double check the package name.  It's not libgccl (with an 'L') it's libgcc1 (number one).

---

### Post by PaulW2U on 2013-10-20
It's a known problem with 32-bit systems:

[http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664]("http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664")

There is a fix:

[https://code.google.com/p/chromium/issues/detail?id=304017#c27](https://code.google.com/p/chromium/issues/detail?id=304017#c27)

But perform at your own risk. ;)

---

### Post by psfal on 2013-10-20
@grmrgd I tried them both already. with the number 1 it says it has no installation candidate, with the letter l it says it can't locate a package.
 
@PaulW2U It looks like they're suggesting the use of the unstable version. I have Chromium, it just won't do some of the brand new flash things, I can wait for the next stable update that has this issue dealt with... Thank you for the info:-)

---

