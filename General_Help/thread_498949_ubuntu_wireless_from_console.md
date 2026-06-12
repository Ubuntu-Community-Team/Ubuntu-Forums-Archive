---
title: "ubuntu wireless from console"
date: 2007-07-12
forum: General Help
---

### Post by Kodfish on 2007-07-12
quick question, what is the underlying wireless daemon? i know it's not wpa_supplicant, but i can't figure out what it is. doesn't seem to be wireless-tools either.

any clues?

---

### Post by kevinlyfellow on 2007-07-12
I'm not sure how to control network manager via commandline, but you should be able to have at least some control over your wireless.  

There are a suite of tools you can use, like iwlist, iwconfig, ifconfig, ifup, ifdown... but I never tried that stuff with network manager running.  I don't know about a daemon, but you can always shut down networking by issuing this command

```
/etc/init.d/networking stop
```

---

