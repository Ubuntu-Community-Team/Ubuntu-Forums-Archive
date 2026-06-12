---
title: "Ubuntu 10.04.4 LTS, agetty process at 100% CPU"
date: 2017-05-04
forum: General Help
---

### Post by snetch2 on 2017-05-04
Hello,

I have an old server with Ubuntu 10.04.4 LTS. It's very slow at moment because of two agetty processes: 

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root     20248  198  0.2 300496 17500 ?        SLl  14:55  40:56 ./agetty -c dxbmkfvan.conf -t 2
root     20249  198  0.2 300496 18056 ?        SLl  14:55  41:02 ./agetty -c dxbmkfvan.conf -t 2
```

When I kill them, they restart after a few minutes. I checked this error for the past hour but can't find a way to disable it. I use SSH to connect to this server. I read that I can edit the /etc/init/tty1.conf file, but I don't have this file. 

I appreciate all suggestions. Thanks, Tim

---

### Post by wildmanne39 on 2017-05-04
I have to point out that 10.04 is no longer supported and especially being a server is at great risk to being hacked, you really should upgrade to 16.04.

---

