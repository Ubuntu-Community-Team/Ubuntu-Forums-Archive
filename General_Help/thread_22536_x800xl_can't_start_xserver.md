---
title: "x800xl can't start xserver"
date: 2005-03-28
forum: General Help
---

### Post by marcaurel on 2005-03-28
My Club3D X800XL (PCIexpress) card can't start the xserver.
The screen turns black 3 times and afterwards I get an errormessage.
I already tried the newest atidriver and newest x.org-packages...
Maybe this can help:
- kernelbootmessage: "cannot allocate resource region 2/0 of device 0000:05:00:0/1"
- xservererrormessage: "fglrx: No matching Device section for instance (BusID PCI:5:0:1) found"

Did anyone out there get a x800xl-card working on ubuntu?

---

### Post by daniels on 2005-03-28
if you don't care about 3d, then the xorg package i'm about to upload will have it working just fine out of the box for 2d with the 'radeon' driver

---

### Post by marcaurel on 2005-03-28
That would be fine!
Where can I find the package when you're finished uploading?

---

### Post by Edgard on 2005-05-20
[QUOTE=daniels]if you don't care about 3d, then the xorg package i'm about to upload will have it working just fine out of the box for 2d with the 'radeon' driver[/QUOTE]
 Which xorg package are talking about??
I'm very interested in it too, but I still don't find a package that solve the problem with my x800xl.

Please HELP!!! :cry:  :cry:  :cry:  :cry:  :cry:  :cry:

---

### Post by daniels on 2005-05-21
That would be the package in Hoary final.  Does it not work?

---

### Post by Edgard on 2005-05-22
[QUOTE=daniels]That would be the package in Hoary final.  Does it not work?[/QUOTE]
 Nope, after the installation I receive this error :

XI0: fatal error 104 (connection reset by peer) on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining

And the x-server can't start.

The only way to start the x-server and Gnome is to use the Vesa driver in 1024*768 max, but with my 21" screen, it's not a very good option :(

---

### Post by Edgard on 2005-05-25
Is it fix in Breezy?
If yes, I will try this version.

---

