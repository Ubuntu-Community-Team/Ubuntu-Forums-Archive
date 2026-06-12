---
title: "Can't update any packages using DPKG/Apt-get update/upgrade"
date: 2016-01-12
forum: General Help
---

### Post by Sam_Clarke on 2016-01-12
Hi all,

Big problem with my Ubuntu install. I can't upgrade anything or install anything new, it seems that my package manager is broken.

Here is the error i get when running apt-get update:

> Architecture: all package 'libvorbisfile3' can't be Multi-Arch: same You may want to run apt-get update to correct these problems

And when running apt-get upgrade:

> 

You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libmono-cil-dev : Depends: libmono-simd4.0-cil (= 3.10.0-0xamarin2) but it is not installed
E: Unmet dependencies. Try using -f.




I've tried using -f and still doesn't work. I think my installation is totally broken but i'm loathed to reinstall everything!

I hope someone has an idea as to what this could be

Sam

---

### Post by Seanan on 2016-01-12
Have you had ubuntu for a while or did this happen right after you installed?

---

### Post by deadflowr on 2016-01-12
> **Sam_Clarke said:**
> I've tried using -f and still doesn't work. I think my installation is totally broken but i'm loathed to reinstall everything!

I hope someone has an idea as to what this could be

Sam

-f?
or
```
sudo apt-get -f install
```
?

---

### Post by mc4man on 2016-01-12
You are using git mono, either pre-packaged or self package built??
mono (3.10.0-0xamarin2) is from here, quite some time ago - 
> mono (3.10.0-0xamarin2) unstable; urgency=medium

  * [2124890] Include missing support-s390x.h header file absent from 
    3.10.0 tarball
  * [e175e7c] Fix missing s390x opcode
  * [36bbb7d] Remove deleted symbols for s390x
  * [ee239bc] Add support for non-assemblies installed to the GAC. This 
    is the first half of a fix to put F# sigdata/optdata files in the GAC.

 -- Jo Shields <jo.shields@xamarin.com>  Wed, 05 Nov 2014 11:49:25 +0000
[https://github.com/mono/linux-packaging-mono](https://github.com/mono/linux-packaging-mono)

---

