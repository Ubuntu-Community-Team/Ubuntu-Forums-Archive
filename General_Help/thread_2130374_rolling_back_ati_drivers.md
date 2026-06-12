---
title: "rolling back ati drivers"
date: 2013-03-29
forum: General Help
---

### Post by John112 on 2013-03-29
Hi,


I installed RadeonDriver and after reboot (after POST) I see only black screen. I can access a terminal with ctrl+alt+f1 but i can't run LXDE.

So my question is how can I rollback drivers to VESA or which ever driver do you recommend for ATI X200 (its an old laptop) ?


Also i don't care about 3D graphics I use that lap just for browsing.

Thanks in advance,
John

edit: I use Lubuntu 10.04 Lucid Lynx

---

### Post by Mark Phelps on 2013-03-29
You should never just force the installation of AMD drivers -- especially as AMD restricted driver support for your card was dropped years ago.

To uninstall the restricted driver and reinstall the open-source Radeon driver, read the material below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by John112 on 2013-03-29
Thanks for fast reply.
Yes I installed open Source RadeonDriver. I haven't found linux binaries for Ati legacy drivers.

The problem is I don't know how to roll back now.

So is there any way (sure there is :) ) to purge open source RadeonDriver and return to VESA?

also I had puppy linux on that laptop before, on which I used xorg package and everything worked great. Is there xorg package for lubuntu?

---

### Post by John112 on 2013-03-29
Ok, solved it simple apt-get remove did it. Still getting used to linux :)

I have another question(s),  I uninstalled **fglrx** and **fglrx-amdccc** and everything is fine now. 

In synaptic I see thath xorg video driver is installed. Should I install open source radeon or leave just leave xorg as it is? Whats the difference?

---

