---
title: "How do I identify my video card - want to install 3d"
date: 2007-02-13
forum: General Help
---

### Post by craig.brisbane on 2007-02-13
Hi all, 

I'd like to have a go at installing compiz/xgl, but how can I find out what my video card is - I'm new to ubuntu and linux - I'm running ubuntu 6.10

Thanks
Craig

---

### Post by Adramelech on 2007-02-13
nano /etc/X11/xorg.conf

and look for a device with a video card name  identifier

---

### Post by highneko on 2007-02-13
lspci | grep -i pci || lspci

---

### Post by craig.brisbane on 2007-02-13
Thank you both for your help. I found that I have a sis, so it looks for what I have read no 3D at this stage.

---

