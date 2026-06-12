---
title: "Dual-Booting Countdown"
date: 2008-04-16
forum: General Help
---

### Post by ivansf92 on 2008-04-16
After I installed Ubuntu using Wubi, when I turn on my computer and it goes to the boot-screen (beginning of this is an example: [http://www.youtube.com/watch?v=2y93IT4aEQk&feature=related](http://www.youtube.com/watch?v=2y93IT4aEQk&feature=related)), the countdown is 15 seconds. However, I want it to be 3 seconds like it was before. (I think this is windows mbr and not grub.)

Does anyone know how to change the countdown time from 15 seconds to 3 seconds?

---

### Post by tommyhakinen on 2008-04-16
open your terminal then enter this :

[QUOTE]
 sudo gedit /boot/grub/menu.lst
{/QUOTE]

enter your password when prompted.
It will open your menu.list under gedit. then look for "timeout" and change 15 to 3.
this should do it.

---

### Post by Nathan_M on 2008-04-16
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by Rainstride on 2008-04-16
you can change it in windows. go to ( control panel\ system\ advanced(tab)\ startup and recovery(settings button) ) there you can edit the wait time to what ever you want, and to show what ever OS you want (as long as there is one).

---

