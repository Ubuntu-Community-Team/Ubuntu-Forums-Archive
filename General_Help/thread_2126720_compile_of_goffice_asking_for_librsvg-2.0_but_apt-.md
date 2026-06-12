---
title: "compile of goffice asking for librsvg-2.0 but apt-get install can't find"
date: 2013-03-18
forum: General Help
---

### Post by dwturner on 2013-03-18
I'd like to install the latest gnumeric, which requires goffice. ./configure for goffice returns

[I]No package 'libgsf-1' found
No package 'librsvg-2.0' found[/I]

apt-get install reports no such packages available, to wit, regarding the first:

[I]Package libgsf-1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libgsf-bin:i386 libgsf-bin libgsf-1-common

E: Package 'libgsf-1' has no installation candidate[/I]

And regarding the second:

[I]E: Unable to locate package librsvg-2.0
E: Couldn't find any package by regex 'librsvg-2.0'[/I]

Please advise.  Many thanks.

Dan

---

### Post by dino99 on 2013-03-18
into the repo, its librsvg2.x

you can download the deb package from:
[https://launchpad.net/ubuntu/+source/gnumeric](https://launchpad.net/ubuntu/+source/gnumeric)

---

### Post by dwturner on 2013-03-21
Ahh. Thank you, thank you, dino99!

---

### Post by dwturner on 2013-03-21
> **dino99 said:**
> into the repo, its librsvg2.x

you can download the deb package from:
[https://launchpad.net/ubuntu/+source/gnumeric](https://launchpad.net/ubuntu/+source/gnumeric)

Sorry, but I'm a novice.

Would you (or someone) translate "into the repo"? I tried apt-get install again with "librsvg2.x", "librsvg2", "librsvg2.0", "librsvg2.1". No joy.

And, I looked at the launchpad link so kindly provided. I'm not confident I follow everything there, but it looks to me that the latest version of Gnumeric, 1.12.1, hasn't been reported to have been installed by anyone on Ubuntu 12.04. (I have an AMD64 machine.)

Is my quest hopeless?

Thanks in advance.

Dan

---

