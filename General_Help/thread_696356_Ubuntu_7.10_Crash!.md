---
title: "Ubuntu 7.10 Crash!"
date: 2008-02-13
forum: General Help
---

### Post by Randybob on 2008-02-13
OK, I recently installed Ubuntu 7.10, and was getting acquainted with the Nexuiz game. The game crashed. Now, I hadn't learned the Ubuntu equivalents of Ctrl-Alt-Esc or Alt-Tab, or Ctrl-Alt-Del. I tried them all just in case, and they didn't do anything, so I hit my restart button. Now Ubuntu won't boot. I told it to boot in recovery mode in GRUB, it seemed to do its equivalent of Scandisk, and it wanted a restart, so it did a soft restart. I tried booting in recovery mode again to finish up whatever needed doing, and it didn't get as far as it did before. It was trying to start Firestarter, and it reported a failure, leaving me with this:

root#

I didn't know what commands to enter, so I hit Ctrl-Alt-Del for a soft restart. I booted back up in Windows, and here I am. 

So, how do I get Ubuntu started again, and in good health? Also, what keys do I hit next time I get a crash to avoid this mess?

---

### Post by mikeize on 2008-02-13
what was the failure?  did it give you any error messages?

---

### Post by Randybob on 2008-02-13
Starting Firestarter . . . [Fail]

What's odd is that earlier in the boot sequence, Firestarter successfully started. :?

---

### Post by mikeize on 2008-02-13
I get the same firestarter failure, almost every boot.  I don't know why, and I'm pretty sure it does start anyway...  so I don't think that is necessarily relevant to your issue, though if you never noticed it before, it may be related.  You could try using the live cd to boot "from first hard drive", or whatever it says.  After a successful boot, perhaps it will fix whatever error.
 
I recently had a power outage cause ubuntu not to boot properly, and I had to manually (recovery console) mount the correct disk as /home.  But for me, there was an error saying that /home couldn't be found.

---

### Post by Foxray on 2008-03-12
You might want to turn off OpenGL 2.0 shader models in the options, it causes some video cards to completely lock up requiring a hard reboot. I play Nexuiz alot and it seems to crash a lot on 2.3, I upgraded to 2.4 and it still locks up after a couple minutes of playing. So I deleted every trace of Nexuiz on my computer, redownloaded the Nexuiz 2.4 file and removed /home/user/.nexuiz or ~/.nexuiz directory.

Tried Nexuiz 2.4 again and no crashes since. This might work for you. I've heard that if there is corruption in of the maps in that directory it causes the game to lock up.

---

### Post by mathgenius on 2008-03-27
Where do I set these shader options ?
Do I need to edit xorg.conf ?

---

