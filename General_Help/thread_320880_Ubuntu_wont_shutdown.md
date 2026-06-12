---
title: "Ubuntu wont shutdown"
date: 2006-12-18
forum: General Help
---

### Post by textguru on 2006-12-18
My ubuntu wont shutdown. I dont know if its just because of my command. Here is the command that I execute:

sudo shutdown -hHP now (it only restarts)

Is power management has something to do with this problem?

---

### Post by NeoLithium on 2006-12-18
wouldn't it have to be in the format ```
sudo shutdown -h -H -P now
``` I'm not sure, but I always thought the options after sudo shutdown had to be individually placed, not lumped together.  I also think that the -h and -H options are redundant, both -H and -P imply -h if you look at shutdown --help...

---

### Post by textguru on 2006-12-18
I have tried what your code but still PC restarts. Hope you have other option.

---

