---
title: "Changing Time at Grub Menu"
date: 2015-04-28
forum: General Help
---

### Post by mandarpowale on 2015-04-28
Hi,

My Ubuntu 14.04.02 Server LTS  dual boots with Windows 8.1 Pro, how do I increase the amount of time it waits before booting at the Grub Menu (Currently it is 10 secs , I would like it to be 30 seconds)

Thanks
Mandar.

---

### Post by dino99 on 2015-04-28
> gksu gedit /etc/default/grub then change '10' by your desired value and then > sudo update-grub

---

### Post by mandarpowale on 2015-04-28
Ty

I will try this out.

ADD: It worked.

---

