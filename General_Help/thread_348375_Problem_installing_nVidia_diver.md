---
title: "Problem installing nVidia diver"
date: 2007-01-28
forum: General Help
---

### Post by PaulFXH on 2007-01-28
Hi
Using Ubuntu Edgy on a Dell Dimension 4550 (2.53 GHz CPU, 1024 MB RAM) with a nVidia GeForce4 MX 420 Graphics card.
Made another attempt to install Beryl on my machine today and found that the nVidia driver installed by the HowTo that I followed (1.0-9746) is not compatible with my graphics card.
As a result, the Xserver couldn't start and I'm now restricted to Recovery Mode in Ubuntu (although the computer is multiboot and I can avail of the GUI in Mepis on the same machine to more readily investigate what might be wrong on the Ubuntu side).

OK, so all I need to do is install a compatible legacy driver. Using Mepis I was able to download the installer for the nVidia driver 1.0-9631 (which IS compatible with my graphics card) to the home folder in the Ubuntu root.

However, I can't get it to install from Ubuntu Recovery Mode using the following code
```
 sudo sh NVIDIA-Linux-x86-1.0-9631-pgk1.run
```
In TTY1, I get the message "Can't open.......".
I also tried Milone's ENVY which also failed to install the driver and gave the message that a NameError occurred as the device is named as " +middlecards{card}" and that the "global name 'middlecards' is not defined".

Anybody know what this is about and what I can do to circumvent it?

---

### Post by PaulFXH on 2007-01-28
Oops..............ignore this

---

