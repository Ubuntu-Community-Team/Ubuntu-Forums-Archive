---
title: "installed vmware xserver will not start"
date: 2008-02-17
forum: General Help
---

### Post by jwlacy72 on 2008-02-17
i recently tried to install vmware on ubuntu 7.10 to get a virtual xp running.  after the install ubuntu
updated vmware and then required a restart, after restarting the xserver will not start.  I tried to sudo apt remove the vmware package but x server still will not start.  any suggestions?

---

### Post by pointone on 2008-02-17
Are any error messages displayed? Check /var/log/Xorg.0.log.

---

### Post by jwlacy72 on 2008-02-17
Warnings:
open /dev/fb0: no such file or directory
open /dev/fb1: no such file or directory
open /dev/fb2: no such file or directory
open /dev/fb3: no such file or directory
open /dev/fb4: no such file or directory
open /dev/fb5: no such file or directory
open /dev/fb6: no such file or directory
open /dev/fb7: no such file or directory
errors:
Unable to find valid framebuffer device
screens found, but none have a usable configuration

---

