---
title: "Increase the size of /var/run  (/run)"
date: 2023-04-09
forum: General Help
---

### Post by wattaman on 2023-04-09
Hi,

It's been a long time since I've setup this Ubuntu 22.04.2 server and I forgot (not exactly a pro here) how I've done it. The tmpfs partition mounted on /run (this should be the physical RAM, right?) is 785M. Sometimes, due to NginX caching (and misconfig most likely) this gets filled. At 100% Nginx crashes so the server is down. I'm mentioning this because the NginX (FPM) caches at /var/run/nginx-cache, so it has to be the it.

I'd like to allocate more than 785M to the virtual partition, but can't find out how. I've been googling for 2 days with no luck.
Sure I'll have to check the configuration as well, but increasing the /run is something I want to do as well.

Thank you.

---

### Post by Holger_Gehrke on 2023-04-09
Does [this]("https://www.man7.org/linux/man-pages/man5/tmpfs.5.html") help ? tmpfs has an option "size=", you can put this in fstab in the appropriate column like this
```

none /var/run tmpfs size=2G 0 0

```
If you already have some option(s)  in the fourth field, remember that option are separated by commas and that there cannot be any white space in a field.

Holger

---

### Post by MAFoElffen on 2023-04-10
Beyond that, if you look in the details of the size= option in man tmpfs, you will see that if you *leave out* the size option, that what it applies as the upper limit that it will dynamically grow to as a default... is "size=50%" of the total memory (RAM).

---

