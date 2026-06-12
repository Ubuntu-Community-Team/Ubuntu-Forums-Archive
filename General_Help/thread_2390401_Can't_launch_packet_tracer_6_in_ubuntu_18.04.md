---
title: "Can't launch packet tracer 6 in ubuntu 18.04"
date: 2018-04-28
forum: General Help
---

### Post by starwars-geek98 on 2018-04-28
Hello all,

I have a problem, I installed cisco packet tracer 6 in my Ubuntu 18.04. But when I try to open it, it won't do anything, from the /usr/bin. From the legit installation folder aka /opt/pt/bin it will tell me that it can't locate a library. It's name is **libcrypto.so.1.0.0. **I tried to install it via the usual way but the system won't allow it. Does anyone knows something for this ? 

Thanks in advance.

---

### Post by d13604f on 2018-04-28
hello star

[COLOR=#000000]#sudo apt-get install libssl1.0.0:i386

#cd /opt/pt/bin

# packettracer

[/COLOR]:cool:[COLOR=#000000]
[/COLOR]

---

### Post by starwars-geek98 on 2018-04-29
Thank you very much!

---

