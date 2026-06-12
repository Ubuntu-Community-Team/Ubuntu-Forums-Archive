---
title: "Vino server refuse to start from command line"
date: 2016-06-05
forum: General Help
---

### Post by Oyvind_Overby on 2016-06-05
I try to start Vino from command line:
root@ubuntu_1604:/usr/lib/vino# vino-server

But all I get is:
vino-server: command not found

Any idea why this isn't working?

---

### Post by steeldriver on 2016-06-05
Because the current directory is not in root's PATH

I'd be extremely wary of starting vino-server as root - what are you trying to do, exactly?

---

