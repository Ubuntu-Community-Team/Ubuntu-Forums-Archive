---
title: "FATAL: Error inserting ndiswrapper"
date: 2006-11-26
forum: General Help
---

### Post by yojimbosteel on 2006-11-26
usagi@tiger-lt:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I am running edgy.

Why?

---

### Post by nictam on 2006-12-05
hi yojimbosteel,

you need to install the version 1.8 of ndiswrapper-util, there should be 2 versions on Synaptic, you probably picked the wrong one, so:

1- uninstall your current ndiswrapper-util
2- install ndiswrapper-util v1.8, it should be in the repos.

I have had the same problem and it worked for me.

cheers, nictam

---

