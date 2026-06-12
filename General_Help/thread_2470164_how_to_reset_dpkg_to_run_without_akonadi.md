---
title: "how to reset dpkg to run without akonadi"
date: 2021-12-20
forum: General Help
---

### Post by antondhdih on 2021-12-20
I am now running kubuntu 20.04 from a buyed USB stick. It is a 32 GB stick, but for using with the overlay FS only a small part of this is available.

the systen had used:

mount -t overlay /cow / -o lowerdir=...,upperdir=/cow/upper,workdir=/cow/work

If I try such command, errors occur: 

"/cow" not a special device.

and "/cow", and arguments to upperdir, workdir are not found in the directory tree.

thus all advices to overlay FS are not applicable.

With the unfortunate ovelay FS I came into the state of "no space on device" errors.

I have deleted very many files in /bin, /usr/bin.
Without help. The overly merged dir, whichvus "/", stays at used 100%.

All what I do does not influence the root "/" to be used 100%.

I am not able to deinstall packages because aptitude, apt-get, dpkg do not work with error message 

"no space left on device".

I have deleted the space consuming akonadi.

now dpkg does not work more. dpkg is dependent on akonadi. Such foolishment. Since ever the package managment utilities had worked without akonadi.

how can I reset dpkg to work independt of akonadi ???.

Regards
anton

---

### Post by DuckHook on 2021-12-26
Duplicate of: [https://ubuntuforums.org/showthread.php?t=2470318](https://ubuntuforums.org/showthread.php?t=2470318)

***Closed***

---

