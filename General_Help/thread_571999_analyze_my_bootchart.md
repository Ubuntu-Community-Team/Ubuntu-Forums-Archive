---
title: "analyze my bootchart"
date: 2007-10-09
forum: General Help
---

### Post by yamzz on 2007-10-09
hello everyone!  my first time to post here.  can anyone help me analyze my bootchart.  maybe i can still cutback on something that i don't need running.  like for instance i have ipw3945 many times during the boot.  

i'm running kubuntu on a compaq presario laptop BTW.  

also my X server seems to start slow.  is there a way to make it faster?  half of the boot time (if it can be considered part of the boot up process) is on starting X server and KDE.  i timed it all and it goes as high as 45-50 seconds.  the first half (20 seconds) you can see in the bootchart image i attached.

thanks!

---

### Post by prince_niceguy on 2007-10-10
Not sure if you have done this already... try doing this...

Open your /etc/init.d/rc file.
sudo nano -w /etc/init.d/rc

Now change the CONCURRENCY variable from "none" to "shell".
CONCURRENCY=shell

and then reprofile your boot sequence.

---

### Post by yamzz on 2007-10-10
ey thanks prince.  :)

yep i have done that already. i read that post somewhere here in the forums on optimizing the boot process.  very good suggestion and it works.   maybe a pointer on making X and KDE start faster?

---

