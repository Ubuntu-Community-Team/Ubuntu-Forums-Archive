---
title: "Power Off Problems"
date: 2007-11-22
forum: General Help
---

### Post by Tsarevich on 2007-11-22
Whenever I power off my computer by System > Quit > Shut Down, after a while, I can see the Ubuntu boot screen that appears for ever but the system does not turn off. How do I resolve this?

Whenever I boot into my system, I have to do:

```
modprobe snd-cs4236
```

to activate my sound card. How do I make it boot with the kernel?

---

### Post by ubuntukerala1980 on 2007-11-22
sudo vi /etc/modules

And add it there


:guitar:

---

