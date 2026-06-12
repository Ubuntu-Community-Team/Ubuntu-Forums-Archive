---
title: "apt-cache: cannot execute binary file"
date: 2007-07-23
forum: General Help
---

### Post by HyperBaton on 2007-07-23
I want to run apt-cache from the console but as you can see I can't. The program is allowed to be executed as you can see by the x flags...

root@hb-laptop:/home/hb# apt-cache
bash: /usr/bin/apt-cache: cannot execute binary file
root@hb-laptop:/home/hb# ls -la /usr/bin | grep apt-cache
-rwxr-xr-x  1 root   root      55384 2007-03-14 18:44 apt-cache

Anyone have any ideas?

---

