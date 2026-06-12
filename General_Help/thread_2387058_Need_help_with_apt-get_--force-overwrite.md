---
title: "Need help with apt-get --force-overwrite"
date: 2018-03-14
forum: General Help
---

### Post by shag00 on 2018-03-14
I am trying to install wine 3.3 devel and found there is an error with one of the dependent packages, libsane1. A bug was filed 6 months ago and a work around was posted in the bug which I do not really understand and can't get to work (error message says 1 option does not work with the other options). Bug [lpbug]1725928[/lpbug]

Specifically, I don't know how "sudo apt-get -o Dpkg::Options:

_":="--force-overwrite" install --reinstall libsane1:i386 (or your real package name)"_

should be written to actually install libsane1 using apt-get. I have the repository and update under control.

Thanks

---

### Post by elephe on 2018-03-17
Just me guessing,

1. I think you download and install this to your computer [https://bugs.launchpad.net/ubuntu/+source/sane-backends/1.0.27-1~experimental3ubuntu     [COLOR=#000000]([/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/1.0.27-1~experimental3ubuntu2")[[COLOR=#000000]sane-backends_1.0.27-1~experimental3ubuntu2.debian.tar.xz[/COLOR]]("https://bugs.launchpad.net/ubuntu/+archive/primary/+files/sane-backends_1.0.27-1%7Eexperimental3ubuntu2.debian.tar.xz")[COLOR=#000000])[/COLOR]
2. Once that is installed retry installing wine.[URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/1.0.27-1~experimental3ubuntu2"]
[/URL]

---

### Post by shag00 on 2018-03-17
After some more guesswork and experiment I discovered that:
```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install --reinstall libsane1:i386
```
is actually the command to use.

What caused me the problem was "::Options::", I had never seen this expression/syntax used before and thought it was something I was supposed to substitute, as it turns out it's meant to be used as is.

---

