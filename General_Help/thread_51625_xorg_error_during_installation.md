---
title: "xorg error during installation"
date: 2005-07-24
forum: General Help
---

### Post by shamxz on 2005-07-24
hi,
when i want start ubuntu live i get a xorg error. the same error i get when i want install the normal ubuntu.
my graphiccard is an ati x800xt pci express.
any solutions?

---

### Post by evilghost on 2005-07-24
So..what's the error?   :razz:

---

### Post by shamxz on 2005-07-25
[QUOTE=evilghost]So..what's the error?   :razz:[/QUOTE]
 hi, 
there stands 
fatal error:
no screens found

---

### Post by Sephen on 2005-07-25
I am getting the same error:

(EE) No devices detected.

Fatal server error:
no screens found

Hardware is as follows:
ATI Radeon X800 PCI-Express
AMD Athlon 64 3200+ venice core
Abit AN8 socket 939 motherboard

---

### Post by shamxz on 2005-07-27
**some help?**

---

### Post by Fed on 2005-08-06
Edit - Just realised you have to be "root" to have permission to change xorg.conf
If you are a LiveCD user, you will have to start it not just by pressing enter but by typing live-expert to get expert mode and root user access.

i had the same prob. here is how you fix it:
xorg will fail to start as you said.

browse to /etc/X11/

do the command "pico xorg.conf"

find the part where it says driver, and says ati, and change ati to radeon.

then do "ps -ax"
in the list, find the line that ends with gdm, and look at the process #

then do "kill #" (where # is the number you got from ps -ax)

then browse to /etc/init.d/

then punch in "gdm"

you should be good to go :)

---

