---
title: "Gusty slow from december"
date: 2008-01-28
forum: General Help
---

### Post by ribico on 2008-01-28
Dear ubuntufriends,
from a month or a little more I am in trouble trying to find out the reason of a sudden change in my system performance.
The system i quite new and fresh installed three months ago, it was really fast.

Ubuntu 7.10 x86_64
Kernel 2.6.22-14
GNOME 2.20.1
AMD 64 X2 Dual Core 5200+

To be more precise, the system is slow especially launching new applications. Once launched they works (it seems) as before.
One of the most annoying thing is when printing.. it takes almost one minute to open the printing dialog, and another minute to print after clicking the button.

'top' shows always a lot of free resources, and just to be sure I removed trackerd.
BTW, not all the applications behave the same, for example NVIDIA X Server Settings panel opens immediately..  why ??

How could I solve without reinstalling ? (I hate the windows way)

---

### Post by jeffus_il on 2008-01-28
Could the slow apps all have network access in common? like the printing dialogs may be searching for network printers ...

---

### Post by ribico on 2008-01-28
No, it is not the case.
Also simply double clicking on a text file takes 30 secs to open ! 
opening a folder directly is fast but clicking on a panel button that opens a folder is very slow..

!?

---

### Post by jeffus_il on 2008-01-28
Have you emptied all the .Trash folders, and do you have any folders with really a lot of files?

---

### Post by articpenguin on 2008-01-28
what filesystem are you using? The only time i got a slowdown was with reiserfs. Reiserfs fragments a lot. I switched to JFS and no more slow downs after 5 months of use. Not sure if the filesystem is related to your slowdowns or not.

---

### Post by PinkFloyd102489 on 2008-01-28
ReiserFS only fragments if you have notail specified in the fstab, which you lose a bit of disk speed  performance if you remove notail.

---

### Post by stchman on 2008-01-28
> **ribico said:**
> Dear ubuntufriends,
from a month or a little more I am in trouble trying to find out the reason of a sudden change in my system performance.
The system i quite new and fresh installed three months ago, it was really fast.

Ubuntu 7.10 x86_64
Kernel 2.6.22-14
GNOME 2.20.1
AMD 64 X2 Dual Core 5200+

To be more precise, the system is slow especially launching new applications. Once launched they works (it seems) as before.
One of the most annoying thing is when printing.. it takes almost one minute to open the printing dialog, and another minute to print after clicking the button.

'top' shows always a lot of free resources, and just to be sure I removed trackerd.
BTW, not all the applications behave the same, for example NVIDIA X Server Settings panel opens immediately..  why ??

How could I solve without reinstalling ? (I hate the windows way)

I had the same problem a while back.  It turns out that the DNS I was using was rotten and my hosts file was all messed up.

Try these.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

then

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

Hope this helps.

---

### Post by ribico on 2008-01-29
WOW stchman.. you saved me !
It was my /etc/hosts file.. I left only 127.0.0.1 and now it goes fast like a tornado !

thanks for support, guys.

---

