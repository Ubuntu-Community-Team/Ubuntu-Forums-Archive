---
title: "Vista and Ubuntu"
date: 2007-02-25
forum: General Help
---

### Post by ali780 on 2007-02-25
Hello
I have Win XP and UBUNTU at the moment. I want to know If I upgrade my windows to Vista, will I lose UBUNTU and I shold install it again or I can keep my ubuntu?
Thak you

---

### Post by cisforcojo on 2007-02-25
Unless VISTA uses a different filesystem and requires you to allocate your ENTIRE drive for VISTA, you shouldn't have a problem, but you should have a LiveCD handy so that you can readd grub to your MBR. I'm sure VISTA will overwrite your MBR. XP does.

---

### Post by ali780 on 2007-02-25
My drives for windows and ubuntu are not same. I mean I have installed windows on C and ubuntu on another partition.

---

### Post by wireddad on 2007-02-25
Yes but like cisforcojo said, Vista will over write the mbr and you will not be able to easily boot into linux without reloading a boot loader.  Now I am not sure if Vista has a built in bootloader that will auto recognize linux or not.  On the safe side, research how to reload Grub.  Or if there is nothing important on the linux partition, just reload linux after upgrading to Vista.

---

