---
title: "Bug in Ubuntu 16.04 LTS"
date: 2016-05-10
forum: General Help
---

### Post by Semn on 2016-05-10
Hi, I have just installed the recent updates from today, and suddenly all text of the icons on the desktop and in the file browser is missing. One can see the icons, but they have no name. Even the Shutdown menu on top has no text, only empty bars and the user-figures. How can one revert changes from today? Is there a command line command?

Thanks!

---

### Post by speartip on 2016-05-10
This was a problem I had occasionally in 14.04 but not so far in 16.04.
Try deleting the fontconfig folder in Home/.cache. Then reboot. That resolved it for me.

---

