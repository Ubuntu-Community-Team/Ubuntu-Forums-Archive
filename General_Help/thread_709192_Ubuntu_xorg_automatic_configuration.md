---
title: "Ubuntu xorg automatic configuration"
date: 2008-02-27
forum: General Help
---

### Post by tropicanamiami on 2008-02-27
Hello,

I need to make an image off an Ubuntu box and deploy it all over the country (more than 150 Desktops), I have configure xorg to use the generic VESA driver which works perfectly with most video cards however after restoring the image on a different box i have noticed the following line in /etc/X11/xorg.conf changes:

BusID "PCI:1:5:0"

So I have to run dpkg-reconfigure xserver-xorg on every box, is there a way to have Ubuntu auto-configure xorg or autodetect the BusID or something like that so X would ALWAYS get up when we deploy these images?

Thank you in advance for the help

---

