---
title: "inotify in Feisty Fawn"
date: 2007-04-11
forum: General Help
---

### Post by peterbengtsson on 2007-04-11
I'm running Feisty Fawn (2.6.20-14-generic) and I want to get inotify working. I can't find a apt package for it. I thought there would be one called inotify-tools ([https://launchpad.net/ubuntu/feisty/+source/inotify-tools](https://launchpad.net/ubuntu/feisty/+source/inotify-tools))

It's probably enabled in my kernel:

```
peterbe@trillian:~ $ grep INOTIFY /usr/src/linux-headers-2.6.20-14/.config 
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
```

What do I need to do to get the software working?

---

