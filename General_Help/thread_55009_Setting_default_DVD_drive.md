---
title: "Setting default DVD drive"
date: 2005-08-07
forum: General Help
---

### Post by kevlar16 on 2005-08-07
I have 2 DVD drives located at '/dev/hdc' and '/dev/hdd'. DVD players like Totem, Xine, and Kaffeine can play DVDs in '/dev/hdc' drive but will not play DVDs in '/dev/hdd'. How do I change the default DVD drive to '/dev/hdd'? 

I have tried this: 'rm -f /dev/dvd && ln -s /dev/cdrom1 /dev/dvd'. And, it works for one session. Each time I reboot the computer, I have to retype this line. Is there a permanent way to do this?

Thanks in advance.

---

