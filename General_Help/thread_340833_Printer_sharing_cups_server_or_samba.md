---
title: "Printer sharing cups server or samba"
date: 2007-01-17
forum: General Help
---

### Post by bward1 on 2007-01-17
I have a network with 4 linux machines (ubuntu, gentoo, centOS) and several windows machines.  I have an epson cx 4200 usb printer hooked up to my ubuntu box and I would like to share that printer with all of the other printers on my network.  I have attempted to get print sharing to work with samba for the windows machines, but the windows clients don't recognize the driver and so they can't work with it.  Is there something special I need to do to get samba to share the driver for windows to be able to use it?  What should I do to share the printer with the other 3 linux computers?

---

### Post by skirkpatrick on 2007-01-17
I've got my HP printer setup to share from both CUPS and Samba.  Here's a couple of things I ran into.

1) Win98 machines seem to print faster using Samba and Linux and XP machines seem to print faster using CUPS.

2) Load the standard Windows driver on your Windows machines and set them up for a network printer.

3) Your Linux box that has the printer should create and share both a raw mode printer and one with the driver.  If your other machines can't talk properly to the driver share, have them use the raw mode share.

---

### Post by nix4me on 2007-01-17
I share my linux printer with cups, via ipp.

You just point the windows and *nix machines to ipp://ip:631.

nix4me

---

