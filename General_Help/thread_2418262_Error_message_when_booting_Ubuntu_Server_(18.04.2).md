---
title: "Error message when booting Ubuntu Server (18.04.2) USB install stick"
date: 2019-05-04
forum: General Help
---

### Post by panja on 2019-05-04
I recently purchased an Intel NUC (NUC8i5BEK) and I'm trying to install Ubuntu Server on this machine.
I've created a bootable USB stick with BalenaEtcher on my MacbookPro. I've tried multiple USB sticks.
Everytime I boot the stick I'm presented with an error:
**Couldn't get size: 0x800000000000000e**

I've already searched and everything I can find about this issue is related to Secure Boot.
I've disabled Secure Boot and put it in Standard Mode (not Custom) and still the error is present when booting the USB stick.

What can be the problem here and how can I fix it?

---

### Post by dino99 on 2019-05-04
Have you downloaded the good bionic image ?
[https://www.ubuntu.com/download/iot/intel-nuc](https://www.ubuntu.com/download/iot/intel-nuc)

---

### Post by panja on 2019-05-04
No I did not.
I'm using Ubuntu Server. The page you refer to is for Ubuntu Core and Desktop as far as I can see.

Also it doesn't mention my model NUC (NUC8i5BEK):
[I]This image is certified for the Dawson Canyon NUC models: 
NUC7i7DNHE, NUC7i7DNKE, NUC7i7DNBE, NUC7i5DNHE, NUC7i5DNKE, NUC7i5DNBE, NUC7i3DNHE, NUC7i3DNKE, and NUC7i3DNBE, 
and for the June Canyon NUC models: NUC7PJYH and NUC7CJYH[/I]

**[update]**
I've noticed that Ubuntu (Server) installs fine (as far as I can see) but I'm a bit worried about the error message.

---

### Post by panja on 2019-05-05
Any one that can help me out?

---

