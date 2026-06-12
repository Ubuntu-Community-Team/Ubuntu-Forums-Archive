---
title: "Is a half-configured &amp; half-installed notice normal?"
date: 2016-05-29
forum: General Help
---

### Post by pfeiffep on 2016-05-29
This is not my main system - it's in a test partition so I have time to dive in to discover the culprit.

This is an Ubuntu 16.04 install first with gnome flash back and then MATE desktop - all prior to official release

Below came from dpkg.log

```
2016-05-06 20:18:30 status unpacked linux-image-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:18:30 status half-configured linux-image-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:19:35 status installed linux-image-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:19:35 configure linux-image-extra-4.4.0-22-generic:amd64 4.4.0-22.39 <none>
2016-05-06 20:19:35 status unpacked linux-image-extra-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:19:35 status half-configured linux-image-extra-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:19:54 status installed linux-image-extra-4.4.0-22-generic:amd64 4.4.0-22.39
2016-05-06 20:19:54 configure linux-image-generic:amd64 4.4.0.22.23 <none>
```

My end game is re-install, but I'd like to learn some more about this and I'm in water over my head :?:

---

