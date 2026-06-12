---
title: "Ubuntu Login Problem"
date: 2008-06-30
forum: General Help
---

### Post by johns4 on 2008-06-30
I just installed Ubuntu 8.04 on a Poweredge 1650. It installed fine, but when I enter in my login name and password and press enter, the system just displays a pinkish looking screen. It has been stuck on this screen for an hour now. Any help?

---

### Post by Mikecore on 2008-06-30
> **johns4 said:**
> I just installed Ubuntu 8.04 on a Poweredge 1650. It installed fine, but when I enter in my login name and password and press enter, the system just displays a pinkish looking screen. It has been stuck on this screen for an hour now. Any help?

sounds like your graphics driver is having issues. try switching to tty2 and login at the prompt. then look at your X server log. located in the/var/log directory.

---

