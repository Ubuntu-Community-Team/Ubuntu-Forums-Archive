---
title: "Trouble with starting up"
date: 2016-08-11
forum: General Help
---

### Post by cltnbatchelor on 2016-08-11
/dev/sda1 contra file system with errors, check forced. 
/dev/sda1: Unexpected inconsistency; run fsck manually.
(I.e., without -a or -p options)
Back with status code 4
The root filesystem on /dev/sda1 requires a manual face
Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash) enter help for list of commands

(Initramfs)

---

### Post by papibe on 2016-08-11
Run the fsck command manually:
```
fsck /dev/sda1
```
Then reboot:
```
reboot
```
Let us know how that goes.
Regards.

---

### Post by cltnbatchelor on 2016-08-11
Thank you that helped now I will be investing some time learning linux and ubuntu. hahah:KS

---

