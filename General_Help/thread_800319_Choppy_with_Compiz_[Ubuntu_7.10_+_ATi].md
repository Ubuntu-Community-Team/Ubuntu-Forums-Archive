---
title: "Choppy with Compiz [Ubuntu 7.10 + ATi]"
date: 2008-05-19
forum: General Help
---

### Post by Kl0wN on 2008-05-19
Hello,

I am on a fresh install of Ubuntu 7.10 Gutsy Gibbon, I installed xgl, and Compiz. 

I followed this guide here - [http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz)

It was fine when I disabled Compiz, but now that I have XGL and compiz enabled, it is choppy in the browser when scrolling, and choppy when loading my desktop. I have a ATi RADEON x700. I also downloaded the updated drivers from the website.

Anyone think they can help me out?

---

### Post by Forlong on 2008-05-19
Remove Xgl when using the latest driver by ATI:
```
sudo apt-get remove xserver-xgl
```

---

### Post by Exsecrabilus on 2008-05-20
> **Kl0wN said:**
> I am on a fresh install of Ubuntu 7.10 Gutsy Gibbon, I installed xgl, and Compiz.
Try upgrading to Ubuntu 8.04 LTS Hardy Heron by going into Update Manager.

---

