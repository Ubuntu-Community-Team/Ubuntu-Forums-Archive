---
title: "Using my own .iso"
date: 2008-04-22
forum: General Help
---

### Post by celtic426 on 2008-04-22
Hi,
I have my own .iso of a modified Ubuntu that my school made.  Is it possible to use Wubi with this?  I put the iso and wubi.exe together in the same folder and tried that but its not looking like it worked.  Please help.  Thanks.

---

### Post by ago on 2008-04-23
Not at this point, please add a bug report in [https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi) and I will add that after release.

It _might_ work only if .disk/info is the same as the one in the Ubuntu CD and if you run wubi with "--skipmd5check".

---

### Post by ago on 2008-04-23
[https://bugs.launchpad.net/wubi/+bug/220905](https://bugs.launchpad.net/wubi/+bug/220905)

---

### Post by celtic426 on 2008-04-23
Cool, I'm glad to know people are working on it even though its not currently supported.  Thanks!

---

