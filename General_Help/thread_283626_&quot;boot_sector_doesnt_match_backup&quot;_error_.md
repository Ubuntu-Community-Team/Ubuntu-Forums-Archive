---
title: "&quot;boot sector doesnt match backup&quot; error on boot"
date: 2006-10-24
forum: General Help
---

### Post by Choad on 2006-10-24
i get an error that sounds something like that when the startup process is checking filesystems. it then says "not automatically fixing this" and goes to a repear console... yay

i skip it with ctrl-d

fixes?

---

### Post by robinl on 2006-10-24
Mine does that since I did a fresh install of Dapper but it doesn't stop the boot process, just shows up whenever I need a filesystem check on boot up. Maybe reconfiguring grub will help?

---

### Post by leona on 2006-10-25
Yep does this on my Ubuntu 64 install as well, no idea what it means or how to fix, but it doesn't stop it loading so assume everything is ok.
Ignorance is bliss.

---

### Post by celsofaf on 2006-11-12
I have exactly the same problem as the original poster, and do exactly the same "solution" to work around. I have no idea how to fix this.

My /boot partition is hdb1, the swap is hdb2, the / partition is hdb3. hda1 runs Windows XP.

The forum search also didn't help me much!... :/

---

### Post by celsofaf on 2006-11-19
Sorry to insist on this, but... Is it possible to have some light over this? :D Thanks!

---

### Post by Choad on 2006-11-19
i just turned off filesystem checks for that partition. edit /etc/fstab and set the last parameter oh whichever partiton is being a bugger to 0

---

### Post by celsofaf on 2006-11-19
All right. Thanks for the help. :)

---

