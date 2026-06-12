---
title: "When Updates Turn Nasty"
date: 2005-10-09
forum: General Help
---

### Post by Mozzer on 2005-10-09
Yesterday I went on to Synaptic (not having done it for a while) to see if there were any updates available. Of course there were - about 90MB of the stuff. So I went and downloaded/installed the lot. Apart from a niggle with Firefox 1.0.7 which I managed to fix, everything seemed fine.

Alas, this morning when I switched on, two major things had changed:

1. My Windows option had disappeared from the grub menu... again. I had to rewrite /boot/grub/menu.lst again. Not a vast problem but slightly irksome.

2. My wireless was dead. The ndiswrapper module refused to load. The wireless card driver for my DWL-510 was still installed but trying to modprobe gave me an error. So my only solution was to uninstall and reinstall Ndiswrapper entirely, which, after the nightmare of making it work when I was a total n00b, I had hoped never to repeat. Of course it wasn't so hard this time but it shouldn't have happened.

Why did these things happen when I updated? And is there any way of preventing it in future?

Thanks in advance,
Mozzer

---

### Post by skirkpatrick on 2005-10-09
The problem with grub happens when you upgrade the kernel.  If you leave your Windows partition info at the end of menus.lst, the upgrade won't touch it.

---

### Post by Hairy_Palms on 2005-10-09
the ndiswrapper probelm is from a kernal upgrade too as the ndis module is compilted to be installed into the kernal running at the time.

---

