---
title: "Microserver hp gen8 with Ubuntu lucid -&gt; no network"
date: 2015-02-06
forum: General Help
---

### Post by drenda on 2015-02-06
Hi guys,
I've an image of my ubuntu lucid that usually I cloned from one microserver to other. With previous version of HP Microserver all worked fine. With this one the network don't work.

Have you some idea how I can solve the problem without reinstall the entire system?

Thanks

---

### Post by drenda on 2015-02-09
Hi, someone have some good hint?

Thanks!

---

### Post by sandyd on 2015-02-09
> **drenda said:**
> Hi, someone have some good hint?

Thanks!

1. This is just a notification to tell you that 10.04 Server will be EOL as of April 2015 and receive no new updates
2. Can you post the output of```

ifconfig
lspci
lsmod
lshw -C network
```

Thanks!

---

