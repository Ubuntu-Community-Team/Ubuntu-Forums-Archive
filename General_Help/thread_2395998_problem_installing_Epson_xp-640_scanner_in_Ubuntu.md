---
title: "problem installing Epson xp-640 scanner in Ubuntu"
date: 2018-07-09
forum: General Help
---

### Post by Seadevil on 2018-07-09
I downloaded the tar file according to instructions and un-tarred the file. But when it got to the install.sh   part in terminal , I get this message:

```
"Unable to locate package libboost-filesystem1.61.0
E: Couldn't find any package by glob 'libboost-filesystem1.61.0'
E: Couldn't find any package by regex 'libboost-filesystem1.61.0'
E: Unable to locate package libboost-program-options1.61.0
E: Couldn't find any package by glob 'libboost-program-options1.61.0'
E: Couldn't find any package by regex 'libboost-program-options1.61.0'
E: Unable to locate package libboost-system1.61.0
E: Couldn't find any package by glob 'libboost-system1.61.0'
E: Couldn't find any package by regex 'libboost-system1.61.0'
dave@primary:~/Downloads/imagescan-bundle-ubuntu-16.10-1.3.23.x64.deb$ 

```
i downloaded and tried to install the tar file and now i am getting this message:  ```
dave@primary:~/Downloads$ tar -zxvf boost1.61_1.61.0+dfsg.orig.tar.xz ./install.sh

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

```

can anyone help ,,?   NEVER MIND ...WAS USING WRONG LIBBOOST VERSION.    PROBLEM SOLVED.

---

