---
title: "What is im-launch ?"
date: 2019-10-18
forum: General Help
---

### Post by rattskjelke on 2019-10-18
I have been using Xubuntu for years and installed 19.10 yesterday.
I noticed a new autostart setting called "im-launch". It executes the following command:
```
sh -c 'if ! [ -e "/usr/bin/ibus-daemon" ] && [ "x$XDG_SESSION_TYPE" = "xwayland" ] ; then exec env IM_CONFIG_CHECK_ENV=1 im-launch true; fi'
```
What is this for? What will happen if I disable it?

---

### Post by uRock on 2019-10-18
Here's the manpage for it. [http://manpages.ubuntu.com/manpages/cosmic/man1/im-launch.1.html](http://manpages.ubuntu.com/manpages/cosmic/man1/im-launch.1.html)

---

