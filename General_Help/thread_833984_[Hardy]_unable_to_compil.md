---
title: "[Hardy] unable to compil"
date: 2008-06-19
forum: General Help
---

### Post by Kasimodo on 2008-06-19
Hello,
I'm on Ubuntu 8.04 and I tried to make a compil but I always have an error with *make* commands... ALL *make*.

error message is Module.symvers is missing....

Of course, I've downloaded headers and sources but always the same problem (Acronis install, v4l install...) So I tried to compil a kernel to see if there is the same problem....

Indeed... it was the same.

Any idea?

Regards,
Kasi

---

### Post by iaculallad on 2008-06-19
Try downloading these files and redo your compiling:

```
sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```

---

### Post by Kasimodo on 2008-06-20
Thank you for your reply but I've already downloaded all these package... I tried onther time and now I've another error message with kernel 2.6.24-19-generic. the same error message than this one:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950")

---

