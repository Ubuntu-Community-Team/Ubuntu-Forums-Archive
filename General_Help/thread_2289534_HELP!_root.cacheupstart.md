---
title: "HELP! /root/.cache/upstart"
date: 2015-08-04
forum: General Help
---

### Post by nbulischeck on 2015-08-04
I just got a notification that my disk was nearly full and thought, how could that be? It was just at 180GB left?

I checked the disk usage analyzer only to see that /root/.cache/upstart had 170GB of storage used!

It's currently filling a log file called ` gnome-session-GNOME ` at ~7MB/s.

It's spamming the line 

"
--> Invalid selection 
--> Invalid selection 
--> Invalid selection 
--> Invalid selection 
--> Invalid selection
"

What do I do?

---

### Post by ruzekle on 2015-08-04
You may be experiencing a known bug. You can go to this source for more help.

[http://askubuntu.com/questions/434581/problem-with-cache-upstart](http://askubuntu.com/questions/434581/problem-with-cache-upstart)

>  You're experiencing this bug [#1240848]("https://bugs.launchpad.net/unity/+bug/1240848").
  I have never on that condition. But, I'm sure It is safe to delete  this dir (or just delete file(s) that's very big). You can also backup  them if not so sure.
  Try ```
sudo apt-get purge logrotate
``` then ```
sudo apt-get install logrotate
```. If this not fixing the problem, then it is possible one of your application (or package) affecting it.
  Many people say that it is periodically occured.
     


---

### Post by nbulischeck on 2015-08-04
Thanks! I purged it and then installed, but it still kept climbing. Decided to reboot as well and when it started back up it seemed fine.

---

