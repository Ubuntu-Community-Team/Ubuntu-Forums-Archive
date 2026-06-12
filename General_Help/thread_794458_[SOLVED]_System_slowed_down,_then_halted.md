---
title: "[SOLVED] System slowed down, then halted"
date: 2008-05-14
forum: General Help
---

### Post by thezood on 2008-05-14
Hi,

I experienced my first Ubuntu crash today. I was surfing in Firefox 2.0.14 and suddenly everything became very sluggish, and then downright ultra-slow. The mouse pointer updated it's position every other second or so and I couldn't close any windows. After a while the entire system became unresponsive. I had quite a few tabs open and an Internet Explorer session in Wine.

I haven't had this problem before but if it happens again, is there anything like CTRL-ALT-DEL in Windows? I tried switching to a console (CTRL-ALT-F1) but it didn't work. Something really ate all my resources. My processor fan started working really hard and it normally only does that in intensive situations. The hard drive also worked like crazy. I made a hard reset and after reboot everything worked fine.

Also, is this something one could expect to show up in any logs? In that case, which logs? It would be nice to be able to track down what went wrong so that I can report some bugs. If not this time, then maybe next time I'll be better prepared. Firefox has been crashing from time to time so that could be the bad guy.

My specs: Ubuntu Hardy x64, 4 Gb RAM, 3Ghz dualcore processor, NVIDIA Geforce 8800. Compiz is turned off.


Regards,
anders.

---

### Post by chrisccoulson on 2008-05-14
The behaviour you describe could be a symptom of an Xorg memory leak or crash. The logs you're interested in are /var/log/Xorg.*, but as they are rotated each time the Xserver starts, you may not have any useful info in them anymore. Also have a look through /var/log/syslog too, just in case anything went in there.

To reboot your system cleanly in this case, you can use the [Magic SysRq combination]("http://en.wikipedia.org/wiki/Magic_SysRq_key") (look in the 'Raising Elephants' section)

---

### Post by thezood on 2008-05-16
This was great help. Thanks!

---

