---
title: "usplash failed"
date: 2007-12-22
forum: General Help
---

### Post by Sportingfan on 2007-12-22
Hi all,

i just installed a "new" monitor (Acer AL1914). Because i could not go to a higher resolution (max 1024-768) i installed the nvidia settings driver. Then in the nvidia settings menu, i choose my monitor and setted the resolution to 1200 x 960. Then a pop-up showed that all users have to log off for the changes to be made. So i rebooted.
At a sudden point of rebooting it stopped and i get the following message:

```

Starting up ...
Loading, please wait...
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600

Ubuntu 7.10 my-desktop tty1

my-desktop login:

```

Can somebody tell me what to do?

I read several threads concerning identical problems but i could not make anything up from those.

thx

---

### Post by Sportingfan on 2007-12-22
I solved the problem by installing other drivers from the command line.
```

sudo apt-get install nvidia-glx

```

---

