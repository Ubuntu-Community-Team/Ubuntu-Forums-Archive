---
title: "Have to reinstall utorrent server 3.3"
date: 2016-11-05
forum: General Help
---

### Post by thorep on 2016-11-05
Hello. Im using this guide to install utserver 3.3 [http://askubuntu.com/questions/530955/how-to-install-utorrent-v3-3-on-14-04](http://askubuntu.com/questions/530955/how-to-install-utorrent-v3-3-on-14-04) .
And it works.
BUT when i reboot my ubuntu 16.04 i cant seem to access web gui no longer. I start utrrent but no luck. I have to reinstall every time i reboot.

Any ideas?

---

### Post by cariboo on 2016-11-05
I don't have uTorrent installed, but did you check to see if was running?

```
ps ax | grep utserver
```

the output should be similar to this:

```
 ps ax | grep grsync
11372 pts/5    S+     0:00 grep --color=auto grsync
31481 ?        Rl    49:41 /usr/bin/grsync -i
```

---

