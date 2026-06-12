---
title: "Computer does not boot 1/2 the time"
date: 2013-01-12
forum: General Help
---

### Post by amazurenko on 2013-01-12
Hello,

I recently installed a quantal on my T61 lenovo thinkpad. I previously had Windows 7 and an older version of ubuntu on the machine, but wiped both. 

The problem I have is this. After I shut down my machine, the next time I try to turn on, when the bootloader is supposed to come up (on a purple background), the purple background appears for about 2 sec, then dissapears, and the computer hangs on a black screen. However, when I do a hard shut down from that and start again - everything works!

What would you recommend?

Previous ubuntu installs (~2011) have not had these problems.

Thank you

AM

---

### Post by lildigiman on 2013-01-12
You could try looking in your boot logs to see what happens?

```
/var/log/boot.log
/var/log/dmesg
```

---

