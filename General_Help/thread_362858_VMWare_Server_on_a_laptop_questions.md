---
title: "VMWare Server on a laptop questions"
date: 2007-02-16
forum: General Help
---

### Post by mthakur2006 on 2007-02-16
Hi all,
I have a Ubuntu 6.06 installation on a Lenovo 3000 C 100 256 MB Ram, 1.6 Ghz processor.(Intel Celeron M). I was wondering if I could run WIn XP Pro inside Ubuntu on the VMWare server. Also, if can I use my phone as a modem (which Ubuntu sees and identifies as a modem, just can't make it work!) and other hardware. i.e. if ubuntu detects them, can the windows make use of it?
Thanks,
Mrinal:KS

---

### Post by alderaan on 2007-02-16
Hi,

You can run Windows inside vmware player or workstation or server, however vmware virtualizes /generalizes hardware, so things that may work will generally be things that you can plug into real parallel ports, serial ports or usb ports, which are than passed through to the virtual ports of the same inside vmware.  

Hardware that is specific to a computer and onboard (like I assume your modem in your laptop) will likely not work.

To give you a more concrete example, your video card can be X, but vmware creates its own virtual card Y, same with network card.

I hope this answers your question..and that I have understood you correctly!

Regards

---

