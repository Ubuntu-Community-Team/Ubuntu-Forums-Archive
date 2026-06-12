---
title: "Not detecting usb device, inserted cds or connecting to the internet"
date: 2007-11-02
forum: General Help
---

### Post by Virgilio on 2007-11-02
i followed these instructions to try and speed ubuntu [http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)
The next time i turned on my computer it started up abit faster BUT then a window popped up saying something like internal error could not not start(or maybe it said open?) HAL. Then i couldnt connect to the internet my usb device wouldnt show up, neither would my inserted dvd's or cd's. So now im on a live session cd. Any way to fix this problem?By the way on live cd everything works fine

---

### Post by Virgilio on 2007-11-02
Umm if this is a duplicate thread than sorry( i thought made this thread 30mins ago..)
Anyway, i tired to speed up my ubuntu by following the instructions here [http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html]("http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html")
The next time i turned on my computer i couldnt conncet to the internt my usb device wasnt showing up and there was a window that pooped up saying something like " Internal error could not start HAL". Any way i coud fix this

---

### Post by cdenley on 2007-11-02
As mentioned in the link you posted, the CONCURRENCY=shell setting in /etc/init.d/rc will cause this problem in Gutsy. Undo the change to this file.

---

