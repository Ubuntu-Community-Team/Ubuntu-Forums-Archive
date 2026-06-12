---
title: "avant window navigator problem"
date: 2008-03-15
forum: General Help
---

### Post by SpikeyMike on 2008-03-15
I need some help :confused: I installed avant window navigator but it wouldn't work properly, I tried to uninstall it using synaptic but got the following error:

[COLOR="Red"]E: /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
[/COLOR]
any advice appreciated....

Spikey

---

### Post by PeterJS on 2008-03-15
Looks like you're trying to install the development version (bzr) of awn over a stable release. The error message is letting you know that the developement version is trying to overwrite portions of the stable version. You sould uninstall the old libawn before installing the bzr version.

---

### Post by SpikeyMike on 2008-04-12
Hi, sorry for the late reaction, please can you tell me how to remove the old version of libawn.....

Regards

Mike

---

