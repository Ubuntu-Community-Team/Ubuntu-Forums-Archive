---
title: "upgrade to 17.10 from 17.04, black screen"
date: 2017-10-20
forum: General Help
---

### Post by alain.roger on 2017-10-20
Hi,
yesterday i upgraded my Kubuntu 17.04 (kernel 4.10.10) to 17.10 (kernel 4.13).
After upgrade i have a black screen. I toggled to terminal mode and discovered that i have no internet connect (wifi without IP) and no graphical session (Desktop Env) while under kernel 4.10.10 everything works well for ubuntu 17.10, under kernel 4.13 bugs for my laptop.

I would like to know if i'm the only one to face this issue and if someone already solved it. I was thinking to upgrade progressively kernel to check where is the issue...but i use a lot flashplayer and i already discovered some compatibility issue with kernel 4.12 and flashplayer so ;m a little bit afraid.

---

### Post by dino99 on 2017-10-20
dev have said such issue is fixed with the next coming 4.13 kernel (wifi problem)
for the 'black screen' it can be due to the graphic used: select a x11 session instead of the default wayland session

---

