---
title: "Emacs missing libMagickWand.so.5 following upgrade?"
date: 2015-05-16
forum: General Help
---

### Post by Stu_White on 2015-05-16
Hello,

I'm a newbie, so apologies in advance if I've missed anything basic here.

I've upgraded from Ubuntu 14 to 15 on my laptop, and Emacs seems to have stopped working. I've uninstalled and reinstalled it using Ubuntu Software Center, using the "GNU Emacs Editor (metapackage)" specifically, but that doesn't seem to have resolved anything. I can launch Emacs from Unity and the program runs correctly, but when I run from the command line I get an error:

$ emacs
emacs: error while loading shared libraries: libMagickWand.so.5: cannot open shared object file: No such file or directory

I've Googled around for this library but haven't been able to track down where I can install it from. One link I found suggested installing it via apt-get but that seems to fail for me, too:

$ sudo apt-get install libmagickwand5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmagickwand5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libmagickwand5' has no installation candidate

It seems like the upgrade has left it in a slightly strange situation, but I'm not clear on how best to fix it. Any help would be appreciated!

Cheers,
Stu

---

