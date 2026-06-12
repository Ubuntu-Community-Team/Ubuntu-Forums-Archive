---
title: "Dual boot options"
date: 2007-10-08
forum: General Help
---

### Post by mark1234 on 2007-10-08
Can anyone advise or supply the correct .lst file to enable both ubuntu & kubuntu to dual boot with Vista? Have tried to follow these instructions, but just get an endlessly scrolling screen looking for the .lst file.

[COLOR="Blue"]Edit C:\wubi\grub\menu.lst: 

Comment out the hidemenu option (put a "#" in front of it, so that the menu is displayed) 

Increase the timeout time (how long the menu is displayed before selecting the default option) 

Copy the last block starting with "title". Each title block is a boot menu entry 

Give an appropriate title to each of the 2 blocks (e.g. "title Ubuntu" and "title Kubuntu") 

Add the kernel paramter "system_virtual_disk=ubuntu.virtual.disk" to the first block and "system_virtual_disk=kubuntu.virtual.disk" to the second one. [/COLOR]

---

### Post by celettu on 2007-10-08
Something I don't understand...are you editing your menu.lst in Windows?

---

### Post by mark1234 on 2007-10-18
yep - editing in wordpad

---

