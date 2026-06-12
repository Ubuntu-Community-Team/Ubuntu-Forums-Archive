---
title: "what is the for libdvd-pkg? I have downloaded it but I don't know it is function"
date: 2019-08-12
forum: General Help
---

### Post by geraygo on 2019-08-12
I am new can you help me? please

---

### Post by Holger_Gehrke on 2019-08-12
From the output of 'apt show libdvd-pkg':
> This package provides libraries that are needed for playing video DVDs
 with a media player (such as VLC, SMplayer, Totem, etc.). It automates
 the process of downloading source files, compiling them, and installing
 the binary packages.


Commercial Video DVDs are partially encrypted so that players whose makers don't have a license by the DVD consortium can't play them. There are libraries to decrypt those disks. In some places these libraries are considered free speech when in source code but illegal tools for breaking copy-protection when distributed as binaries. To get around this, libdvd-pkg  downloads the source for the libraries and compiles it.

You can install the package with a simple 'sudo apt install libdvd-pkg' in a terminal. No need to download it separately, apt does the downloading and installing.

Holger

---

