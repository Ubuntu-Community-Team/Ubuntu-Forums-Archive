---
title: "glibc-2.3.2.ds1-20ubuntu13"
date: 2005-09-26
forum: General Help
---

### Post by Vinze on 2005-09-26
Does anyone happen to have a .deb of glibc-2.3.2.ds1-20ubuntu13? I can't find it on packages.ubuntu.com and it's not in my reprositories (well that's quite logical). But I really need it because I had to deinstall ubuntu-desktop before, now I want to reinstall it but it says it depends on glibc-2.3.2.ds1-20ubuntu13, which I can't download! Please help!

---

### Post by lithorus on 2005-09-27
Did you remember to do a apt-get update?

EDIT:
glibc is a virtual package provided by the libc6 package. I find it hard to beleive that you don't have libc6 installed :)

---

### Post by Vinze on 2005-09-27
[QUOTE=lithorus]Did you remember to do a apt-get update?

EDIT:
glibc is a virtual package provided by the libc6 package. I find it hard to beleive that you don't have libc6 installed :)[/QUOTE]
Well, indeed, I have libc6 installed, but that doesn't mean I don't have the error... I don't have libc6-dev installed, but when I do sudo apt-get install libc6-dev I get:

```
vincent@vincent:~$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-22 is to be installed
E: Broken packages

```

---

