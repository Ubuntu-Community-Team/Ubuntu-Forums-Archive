---
title: "I cant shutoff my computer"
date: 2016-01-16
forum: General Help
---

### Post by scriptkitten_ on 2016-01-16
Whenever I try to shutdown my computer I get this error


Failed to start poweroff.target: Transaction is destructive.


Help?????

---

### Post by vilwarin on 2016-01-26
Same problem here.

> shutdown -h now
yields
> Failed to start poweroff.target: Transaction is destructive.

There seems to be no solution online so far. Any ideas?
> poweroff -f 
does work, but I'd like to be able to shutdown Ubuntu properly and not just cut the power.

---

### Post by kansasnoob on 2016-01-26
Sounds like it may be because a suspend task is still active. Bugs have been filed both in launchpad and upstream:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1441253](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1441253)

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=776171](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=776171)

---

### Post by vilwarin on 2016-01-26
Hi kansasnoob,

thank you for your answer :)
Do you know, how I can find out if this bug applies to our situation?
I.e. how does that suspend task look like. Can I see it with **ps**?

If so, the easiest solution will be to simply kill the suspend task by it's pid. What do you think?

---

### Post by kansasnoob on 2016-01-28
I'm not sure but I'll give you a free bump so some fresh eyes can have a look.

---

### Post by vilwarin on 2016-01-30
So for everyone stumbling upon this, here is a workaround until this bug is fixed.

Check that you are suffering from this bug (hanging suspend task) by running
> ps aux | grep suspend
you should see something like
> root      3651  0.0  0.0   8668  1716 ?        Ss   07:18   0:00 /lib/systemd/systemd-sleep suspend

Then if you want a proper shutdown of your sysem:
Frist logout of the graphical desktop environment, then switch to a tty console (ctrl + alt + f1) and stop the window manager. Most likely lightdm
> sudo service lightdm stop

Now you can kill that suspend job:
> sudo kill -9 3651
Note: replace 3651 with the job id you got from ps aux.

It might be that your system will process a pending shutdown task, if not running:
> sudo shutdown -h now 
should work now.

Good Luck!

---

