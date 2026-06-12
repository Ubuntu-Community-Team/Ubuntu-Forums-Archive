---
title: "Trouble booting up after forced shutdown."
date: 2013-01-04
forum: General Help
---

### Post by gavinflud on 2013-01-04
I've had Ubuntu 12.10 running smoothly for over three months now, but today it go stuck on the login screen and wouldn't recognise any keyboard or mouse actions.

I forced it to shutdown and turned it back on again, but now am greeting with a simple terminal screen saying:

```
error: attempt to read or write outside of disk 'hd0'.
grub rescue>
```

Anybody got any ideas what's causing the issue or how to solve it? Any help is much appreciated.

---

### Post by gavinflud on 2013-01-04
I seem to have fixed the problem by ejecting the cd-drive and then restarting.

I'm still confused as to why I was getting that error in the grub terminal, and also why it wasn't recognizing my keyboard or mouse originally. It's working fine now but I'll have to keep looking to see what the real cause of it was.

---

### Post by Rocklobster690 on 2013-01-04
This might help: [http://goo.gl/4Jyy](http://goo.gl/4Jyy)    Good Luck.

---

### Post by gavinflud on 2013-01-04
> **Rocklobster690 said:**
> This might help: [http://goo.gl/4Jyy](http://goo.gl/4Jyy)    Good Luck.

Thanks for that, actually came across it this evening while searching for an answer to the problem. It's an unusual one because, even after following advice from people on other forums, there doesn't seem to be anything odd or out of place in my grub configuration.

I'll have another glance through that page though. Thanks again.

---

