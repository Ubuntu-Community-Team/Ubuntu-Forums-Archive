---
title: "Help..just installed 5.10, boot up.. goes dead"
date: 2005-10-18
forum: General Help
---

### Post by zul_qarnain on 2005-10-18
Hi,

I just installed Ubuntu 5.10. Everything seemed to go well. However, when I try to boot up, after I log on the screen just turns brown and then nothing happens. I can move the mouse pointer around, but there are no menu items to click. 

Any suggestions as to how to starting solving this?

I use mostly unix/solaris at work, but I so wanted Ubuntu to take me away from windows at home. Sigh.

-zq

---

### Post by Murgle on 2005-10-18
can you tell us the output of 'cat /var/log/Xorg.0.log'  you can hit Crtl + Alt + F2 to get to a terminal.  I susspect that it will complain about bad hsync and vert refresh rates.  If this is the case then type sudo nano /etc/X11/Xorg.conf and go change the rates to a valid value.

---

