---
title: "Partitioning"
date: 2005-10-12
forum: General Help
---

### Post by vr04 on 2005-10-12
I just did a fresh 5.04 install and created 3 partitions. One of them is about 10GB and holds the OS, another is 45GB and mounted under /files and a third, which is the swap.

My question is, will I be able to keep the '/files' partition in order to save stuff that I want to keep and wipe or format the / partition (which holds ubuntu itself) if I want to do, say, a fresh install of Breezy, or some future release.

Thanks in advance.

---

### Post by aysiu on 2005-10-12
Traditionally people have a /home partition that's separate, which has both files and settings. It sounds as if you have a separate partition for just files. Yes, you can preserve it, but I'd say you should make that your /home partition, too...

---

### Post by jamesstansell on 2005-10-12
[QUOTE=vr04]I just did a fresh 5.04 install and created 3 partitions. One of them is about 10GB and holds the OS, another is 45GB and mounted under /files and a third, which is the swap.

My question is, will I be able to keep the '/files' partition in order to save stuff that I want to keep and wipe or format the / partition (which holds ubuntu itself) if I want to do, say, a fresh install of Breezy, or some future release.

Thanks in advance.[/QUOTE]
Yes, you certainly should be able to.  You might find some documentation that refers to a partition like that as /home.

Doing a dist-upgrade will easily preserve your partitions, as well as your configuration information.

---

### Post by vr04 on 2005-10-12
sounds great. my main concern is to keep my files, such as my mp3s. OS settings are not that important to me because i do screw up stuff because i'm still learning about linux. i've done many fresh installs up til now, mainly due to my experimenting and breaking stuff.

in the future, if i do a clean install, i just want to be able to reinstall the os on my smaller partition and be able to mount /files in order to have my saved files (mp3s) handy, right after the fresh install.

---

### Post by jamesstansell on 2005-10-12
[QUOTE=vr04]sounds great. my main concern is to keep my files, such as my mp3s. OS settings are not that important to me because i do screw up stuff because i'm still learning about linux. i've done many fresh installs up til now, mainly due to my experimenting and breaking stuff.

in the future, if i do a clean install, i just want to be able to reinstall the os on my smaller partition and be able to mount /files in order to have my saved files (mp3s) handy, right after the fresh install.[/QUOTE]
Of course, the old saying about "if it's important, keep a backup" probably still applies!

---

