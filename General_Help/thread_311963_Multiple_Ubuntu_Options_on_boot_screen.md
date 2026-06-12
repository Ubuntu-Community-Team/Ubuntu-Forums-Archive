---
title: "Multiple Ubuntu Options on boot screen"
date: 2006-12-03
forum: General Help
---

### Post by Sprite1990 on 2006-12-03
On the boot screen it gives me 4 Ubuntu options which are roughly:

Ubuntu 2.6.17-10 Generic
Ubuntu 2.6.17-10 Generic Safe Mode
Ubuntu 2.6.17-10 386
Ubuntu 2.6.17-10 386 SAfe Mode

WHat can I edit to get rid of the two 386 options ? (I booted into the Generic one and everything is fine and dandy)

---

### Post by bapoumba on 2006-12-03
You can remove them from synaptic.
But ... It is always safer to keep at least one other kernel which you know is running fine, just in case of an unfortunate update ;)

---

### Post by Sprite1990 on 2006-12-03
Also is it possible to give the boot up page a GUI ?

---

### Post by Game_Ender on 2006-12-03
Yes, search for gfxgrub in the how to section to get yourself a graphical grub screen.  I am looking for something similar to the blue theme but with the classic ubuntu orange.

---

### Post by klsmith259 on 2006-12-03
You can keep the kernels installed and edit /boot/grub/menu.lst

I would keep the regular generic kernel and the (safe mode) kernel incase something happens.

---

### Post by Sprite1990 on 2006-12-03
> **bapoumba said:**
> You can remove them from synaptic.
But ... It is always safer to keep at least one other kernel which you know is running fine, just in case of an unfortunate update ;)

Where abouts in Synaptic are they ? Cant find them ><

---

### Post by bapoumba on 2006-12-03
Should be linux-image-386, but once again, just keep it. You  could remove it after next kernel upgrade if everything is fine. (I always keep current (say version n) and previous (say version n-1) kernels).

---

