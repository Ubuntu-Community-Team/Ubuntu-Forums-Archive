---
title: "Edited /etc/modules - Hanging at boot"
date: 2006-11-16
forum: General Help
---

### Post by Verminox on 2006-11-16
My PS/2 mouse was not being detected in Kubuntu 6.06 LTS so I searched google for similar problems and found one thread on a forum (I lost the link) that directed to edit the /etc/modules file. My file consisted of:


```
#various comments
lp
psmouse
```

I changed it to

```
#various comments
lp
psmouse proto=exps
```

Of course I had no idae hat that meant and I am very new to linux systems so it was stupid of me to try it out but well yeah.. I did it.

Now on boot the Kubuntu splash starts up.... everything seems to load "OK" and then instead of seeidn KDE loaded all I see is the Kubuntu logo (the splash that usually comes up at boot) and an empty bar below it, and no other text. It just gets stuck there. 

So I tried booting with recovery mode and I found myself in the console. I tried editing the file with:
sudo -e /etc/modules

But it still says cannot overwrite file - permission deined.

How do I edit the /etc/modules file via console? And more importantly, will this solve the problem or has the editing of that file got nothing to do with the boot problems?

---

### Post by 23meg on 2006-11-16
```
nano /etc/modules
```should do. Remove what you added and see if the problem goes away.

---

