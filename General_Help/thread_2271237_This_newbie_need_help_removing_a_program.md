---
title: "This newbie need help removing a program"
date: 2015-03-28
forum: General Help
---

### Post by brent20 on 2015-03-28
Hi,

I am dual booting win 8.1 / Ubuntu 14.04 and on windows I've been using F.lux for a long time, so also wanted to use It on Ubuntu. I installed it from: [https://justgetflux.com/linux.html](https://justgetflux.com/linux.html)

I copy and pasted the lines of code and it installed, however it didn work so I installed Redshift form the software center. Now I want to remove Flux but I can seem to figure out how. 

I tried: 
sudo rm /usr/bin/xflux

and

sudo rm /usr/bin/fluxgui

But it didn do anything.

Any suggestions?

---

### Post by steeldriver on 2015-03-28
Since it was installed as a packged via a PPA, you should be able to reverse the steps using

```

sudo apt-get remove --purge fluxgui

sudo add-apt-repository --remove ppa:kilian/f.lux

```

---

### Post by brent20 on 2015-03-28
Yup, that did the trick.

Thanks ;)

---

