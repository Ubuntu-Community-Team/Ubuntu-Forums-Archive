---
title: "How to open .msi"
date: 2007-05-04
forum: General Help
---

### Post by pisio on 2007-05-04
HI for all.
How I can open file.msi
I like installing PhotoShop(Cs3) and Dreamweaver CS3.
I don't  want working whit GMIP.
Whit  Wine 0.9.33 don't opening .msi
10X
Edit://
My O.S. is UBUNTU 7.04
10x agin

---

### Post by fnf on 2007-05-04
With Windows applications you have several choices:
[LIST]
[*]Virtual Machine: Installing a copy Windows in a VM then install Photoshop there. A few user-friendly VMMs are VMware, qemu, Parallels and VirtualBox.
[*]Windows Complatibility Layer: WINE, works on many cases.
[*]Remote Desktop: If you've got a spare Windows machine, set it up as a Terminal Server and connect to it with rdesktop: Take a look at [SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization")
[/LIST]

Using a VM is probably the best, now if you don't want all the hassle: Either learn to use GIMP (btw, it -is- user-friendly, provided that you don't consider it as a PS-clone; ditto Linux is not a Windows-clone) or dual-boot.

With regards to WINE: you can run *.MSI with msiexec.

---

### Post by pisio on 2007-05-04
10x ;)

---

