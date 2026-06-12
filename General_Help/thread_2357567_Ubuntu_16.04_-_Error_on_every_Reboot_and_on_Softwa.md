---
title: "Ubuntu 16.04 - Error on every Reboot and on Software Updater"
date: 2017-04-03
forum: General Help
---

### Post by linux.girl on 2017-04-03
Hi everyone,

Ever since I upgraded to 16.04 LTS (internal upgrade), I have been experiencing all sorts of problems with software updater and reboot. Software updater now runs fine, but gives me error every time. And on reboot, after each sw update, I get different errors. Please see the screenshots.

Any ideas what could be causing this? Every time it is a different error. It doesn't stop me from working but tells me my system is not healthy and I want to troubleshoot but dont know how.

Can you assist please?

Million thanks in advance!

---

### Post by RobGoss on 2017-04-03
Hello and welcome, try running the following command to see it that helps

```

sudo apt-get update
```

```

sudo apt-get upgrade
```

---

### Post by linux.girl on 2017-04-04
Hi RobGoss,

Thank you for the tip - I did that already a few times but every time I boot a different error appears. It always says ubuntu suffered an internal error, do you want to report, etc, I always report, every time is a different thing. After I report everything runs as "usual" but again, these errors at every boot concern me because it means the system is not healthy and I want to get to the root cause of this.

I also needed to remote desktop to my ubuntu so I followed this guide [http://www.technig.com/remote-access-windows-10-via-ubuntu-vise-versa/](http://www.technig.com/remote-access-windows-10-via-ubuntu-vise-versa/) and without noticing it installed xfce4 desktop environment and I can't for the life of me figure out why there was a need to install a different desktop environment to remote desktop - any idea why? If I un-install xfce4 will the remote desktop stop working?

I realize I mixed two different issues in one same thread, but the errors are really my main concern.

Many thanks!

---

### Post by RobGoss on 2017-04-04
I'm assuming when you installed 16.04.2 it had the defult Unity desktop environment correct?

And you installed XFCE4 correct?

If you are experiencing these problems after installing Xfce4 desktop environment I would simply remove that desktop environment and see if the problems still persist

---

### Post by linux.girl on 2017-04-05
Exactly. But the errors were happening before that. And the funny thing  is: I get XFCE4 environment only on the login screen. After I enter my  password, the environment still looks and behaves like Unity desktop.  And more than that, I did a few reboots and I am not getting any errors  of the kind "ubuntu experienced an internal error, please report, etc".  Can't explain why but I am sure these errors will return so I will keep  this thread open so I can post which erros I see. Thanks!

---

### Post by RobGoss on 2017-04-05
You're are very welcome **Linux.girl** receiving errors like that can be caused by a number of things if they return just let us know I'm sure we will be able to figure thinks out for you

Have a great day

---

