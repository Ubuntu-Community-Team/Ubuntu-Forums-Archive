---
title: "&quot;sudo shutdown now&quot; drops to root console"
date: 2006-10-30
forum: General Help
---

### Post by 505 on 2006-10-30
When I enter the command "sudo shutdown now" the X server is killed and I'm dropped in a root shell. Before that is a message 'init: rc1 process kill by signal 15'. When I type 'exit' in the root console the X server starts again.

Is this the intended behaviour. Should the system just shut down by default when issuing this command?

---

### Post by kaamos on 2006-10-30
```
sudo shutdown -h now
```

should halt the system.

---

### Post by 505 on 2006-10-30
> **kaamos said:**
> ```
sudo shutdown -h now
```

should halt the system.
Yeah, I know the switch -h halts the system completely. It's more that I wanted to know if it should go into root console if I don't use any switch.

If I recall correctly, earlier versions did shut down when using shutdown without any switches.

---

### Post by bsussman on 2006-10-30
The 6.06 manpage documentation: "...runlevel 1 is used to put to system into a state where  admin istrative tasks can be performed; this is the default if neither the -h or -r flag is given to shutdown..."

For 6.10 "If no options are given, the maintenance event is sent."  which is about the same thing.

I verified behavior in 6.10 but on my desktop 6.06 seems to be trying to do the documented thing but gets hung up after sending sigterm - since I never use the feature, I am not inclined to troubleshoot. :mrgreen:

---

