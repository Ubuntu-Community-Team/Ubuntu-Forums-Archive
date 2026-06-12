---
title: "Cannot install ffmpeg"
date: 2015-08-23
forum: General Help
---

### Post by andfree on 2015-08-23
```
sudo apt-get install ffmpeg
```

Output:
```
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate
```

Lubuntu 14.04, Firefox 40.0

---

### Post by monkeybrain20122 on 2015-08-23
ffmpeg is not in 14.04's repo. It was replaced by a fork called avconv. But it comes back in 15.04

  To install ffmpeg in 14.04 use either [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (ffmpeg static) or [https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6) (ffmpeg shared)

---

### Post by andfree on 2015-08-23
I used the first one and it worked. Thanks a lot.

---

