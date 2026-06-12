---
title: "How to upgrade ubuntu but not the kernel"
date: 2019-01-17
forum: General Help
---

### Post by cazz on 2019-01-17
Maybe is a easy way but is that possible.
I have some hardware that is not so easy to use on the latest version of the kernel.

---

### Post by Andreyshel on 2019-01-17
I believe [apt-mark]("http://manpages.ubuntu.com/manpages/bionic/man8/apt-mark.8.html") is the thing you are searching for.
[Ask Ubuntu]("https://askubuntu.com/questions/938494/how-to-i-prevent-ubuntu-from-kernel-version-upgrade-and-notification") has more detailed answer.[URL="http://manpages.ubuntu.com/manpages/bionic/man8/apt-mark.8.html"]

[/URL]

---

### Post by #&amp;thj^% on 2019-01-17
^^^^^+1 And you can freeze any package including kernel packages by "sudo apt-mark hold <package_name>"

for example:
```

sudo apt-mark hold linux-image-generic linux-headers-generic
```
[COLOR="#FF0000"]***IMPORTANT***[/COLOR]
But you need to check which kernel meta-package is installed for LTS versions. It may be linux-generic-lts-bionicc, example only.

Clue:
```
apt search linux-image-generic linux-headers-generic
```

---

