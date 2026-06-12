---
title: "How do I stop xserver from starting automatically?"
date: 2006-09-08
forum: General Help
---

### Post by Hyperonic on 2006-09-08
I don't need a desktop most of the time, so, figuring out how to stop xserver (and effectively Gnome) from starting automatically with Ubuntu.

Someone told me to edit /etc/inittab, but, I ended up making the system automatically shutdown. :-p

I fixed that, though. :-)

But, how would I go about doing this?

---

### Post by jocko on 2006-09-08
I think the xserver is started by gdm (ubuntu) or kdm (kubuntu). If you disable the startup script that starts gdm it will not start automatically during boot.
I think this can be done by renaming all links named S13gdm to s13gdm (they are only used if their name start with capital S). You should find them in /etc/rc2.d through /etc/rc5.d.
I'm not sure if there are any other startup (or shutdown) scripts that you would need to disable to aviod errors.

---

### Post by Ramses de Norre on 2006-09-08
It's safer to use sysv-rc-conf to disable init scripts.

---

### Post by Hyperonic on 2006-09-08
> **Ramses de Norre said:**
> It's safer to use sysv-rc-conf to disable init scripts.

How would I go about doing that?

---

### Post by Ramses de Norre on 2006-09-08
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Uncheck services you want to stop on the needed runlevels with the space bar and press q to exit.
Services are easy to restore then.

---

### Post by Hyperonic on 2006-09-08
Thank you. :-)

---

