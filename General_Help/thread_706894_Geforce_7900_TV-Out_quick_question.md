---
title: "Geforce 7900 TV-Out quick question"
date: 2008-02-24
forum: General Help
---

### Post by tirux on 2008-02-24
After tweaking the xorg.conf file I really don't want to install the restricted driver from nvidia. However, I want to watch movies with TV-Out...

Is there an alternative to use TV-Out? It's kinda interesting that while booting my computer, I can see it from my TV without any problems. But once I get inside Ubuntu, weird colors shows up in the whole screen.

And if I HAVE to use restricted driver, would I still be able to modify the xorg.conf file?

---

### Post by overdrank on 2008-02-24
> **tirux said:**
> After tweaking the xorg.conf file I really don't want to install the restricted driver from nvidia. However, I want to watch movies with TV-Out...

Is there an alternative to use TV-Out? It's kinda interesting that while booting my computer, I can see it from my TV without any problems. But once I get inside Ubuntu, weird colors shows up in the whole screen.

And if I HAVE to use restricted driver, would I still be able to modify the xorg.conf file?

HI and what driver are you using in the xorg? If you are using the nvidia driver the you could use the nvidia-settings ```
gksudo nvidia-settings
``` And yes if you use the restricted driver you can edit your xorg although you may not have to.:)

---

### Post by tirux on 2008-02-24
I am currently using the "nv" driver in my xorg file. However, nothing happened typing in terminal "gksudo nvidia-settings".

The main reason I don't want the restricted driver it's because it somehow changes my resolution 96 dots per inch size to only 86 dots per inch.

---

