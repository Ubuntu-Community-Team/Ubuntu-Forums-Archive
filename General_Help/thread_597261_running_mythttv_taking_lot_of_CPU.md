---
title: "running mythttv taking lot of CPU"
date: 2007-10-30
forum: General Help
---

### Post by Green_Star on 2007-10-30
Normally  when idle my cpu runs around 2-5% but when i run mythtv it is almost 100%, in that mythtv itself talking 75-80% of cpu. even i minimized the mythtv window the cpu still at around 100%. is it normal? i do not want to see my cpu running 100% all the time. any suggesstion? is it because of my display drivers? i am not using proprietary drivers for now and has ATI Readon X1300. with PVR-150 tuner

---

### Post by kah00na on 2007-10-31
check out your hd disk parameters.  You may not have something set correctly.  Here's a website that may help you out with this.  The command to test and change the parameters is "hdparam".

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html")

Other things that can cause the high CPU is not having a good video card to display the video or it could be that you don't have enough memory so the cpu is busy doing swapping of memory.  I'd start with the harddrive first though.

---

