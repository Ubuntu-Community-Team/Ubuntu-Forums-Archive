---
title: "LiMe memory dump only works through console not SSH"
date: 2021-12-21
forum: General Help
---

### Post by nazgulnr5 on 2021-12-21
Hi there,
I'm trying to generate a LiMe memory dump on an Ubuntu Server (20.04).
The command I use is *sudo insmod lime-5.4.0-81-generic.ko "path=/usr/src/lime-forensics-1.9-1ubuntu0.3/test.mem format=lime”*
with lime-5.4.0-81-generic.ko being the kernel module generated with make.
This works fine through console but when I run the same command through SSH it hangs with a ">" prompt and nothing else happens. No file is created.
Any ideas why it's not working over SSH?

---

