---
title: "ubuntu 16.04 black screen after shut down"
date: 2016-10-01
forum: General Help
---

### Post by 2ben on 2016-10-01
Someone please helps me.
I deleted my window 7 HP and installed ubuntu  16.04 on it with LVM option using bootable USB.

I installed successfully and could play around with it. 
Then opened terminal, updated and upgraded.
I shut down my ubuntu and attempted to reopen it.

What i got is black screen and couldn't go into any menu or any login.

Could someone give me any instruction how to fix it?:icon_frown::icon_frown::icon_frown:

---

### Post by ajgreeny on 2016-10-02
We need a lot more information than you have given us in order to be able to give you any help, otherwise we are all just shooting in the dark.

CPU?
RAM?
Graphic card?

If you can press Ctrl+Alt+F1 at your black screen, you may get to a command line at which you can login with your username and password, the latter of which will not show on screen; just type it carefully and press Enter.  

If that logs you in use command ```
inxi -F
``` which will tell you a lot about your machine, and whilst it will be difficult to copy and paste that back here it will let you see what you have and you can then tell us.

For future questions you may have see [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by 2ben on 2016-10-02
Thank you for your information.
It turns out that just my laptop screen was connected badly to the screen via VGA.
It is fixed now.

---

