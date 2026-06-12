---
title: "Ubuntu Shutdown Scripts - how to customize them?"
date: 2007-05-07
forum: General Help
---

### Post by ariel on 2007-05-07
Hi,

    I need to automate the execution a command (killall -SIGHUP java) when my machine shuts down, but *before* GDM ungracefully kills all applications upon exit.

   Attaching this command to the script that Ubuntu runs when the Shutdown button is pressed would be OK. I have no clue how to find this script, could someone give me a hint?

    Another alternative would be to somehow tie this to GDM's shutdown process. I actually found how to configure a shutdown script via gdm.conf, however, gdm runs the "shutdown script" after all the applications were killed, so it didn't help. Perhaps someone knows how to have GDM run a script on shutdown but *before* it starts killing the open apps?

Thanks!

---

### Post by dcstar on 2007-05-08
> **ariel said:**
> Hi,

    I need to automate the execution a command (killall -SIGHUP java) when my machine shuts down, but *before* GDM ungracefully kills all applications upon exit.

   Attaching this command to the script that Ubuntu runs when the Shutdown button is pressed would be OK. I have no clue how to find this script, could someone give me a hint?

    Another alternative would be to somehow tie this to GDM's shutdown process. I actually found how to configure a shutdown script via gdm.conf, however, gdm runs the "shutdown script" after all the applications were killed, so it didn't help. Perhaps someone knows how to have GDM run a script on shutdown but *before* it starts killing the open apps?

Thanks!

When you select shutdown then the items in /etc/rc0.d are run (rc6.d for a reboot).

The "K" items (all links to /etc/init.d scripts) are run in numerical order to end the relevant processes in an orderly fashion, you can create your own script and run it where-ever in the order you like.

---

### Post by ariel on 2007-05-08
Hi dcstar, thanks for your answer.

In both rc0.d and rc6.d there is a shortcut like this: **K01gdm**

So what I did is open /etc/init.d/gdm, and in the **stop** part of the script, added the killall command, like this:

...
  stop)
   ** killall -SIGHUP java    **
    log_begin_msg "Stopping GNOME Display Manager..."
    start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
    log_end_msg 0
...


Unfortunately, the killall is not done and java stays up while gdm disappears. If, inside GNOME, I just open a terminal and type the command, then java exits as expected. This is what I'm trying to automate right before shutdown/reboot. 

Any clue?

Thanks!

---

### Post by dcstar on 2007-05-09
> **ariel said:**
> Hi dcstar, thanks for your answer.

In both rc0.d and rc6.d there is a shortcut like this: **K01gdm**

So what I did is open /etc/init.d/gdm, and in the **stop** part of the script, added the killall command, like this:

...
  stop)
   ** killall -SIGHUP java    **
    log_begin_msg "Stopping GNOME Display Manager..."
    start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
    log_end_msg 0
...


Unfortunately, the killall is not done and java stays up while gdm disappears. If, inside GNOME, I just open a terminal and type the command, then java exits as expected. This is what I'm trying to automate right before shutdown/reboot. 

Any clue?

Thanks!

Find the full path to "killall" and put that in your script:
```
whereis killall
```

---

### Post by ariel on 2007-05-09
I replaced killall with /usr/bin/killall.... no change in behavior :(, still the same problem
There must a way to automate this :confused: ....

---

### Post by ariel on 2007-05-10
Something I could verify: the command I added to /etc/init.d/gdm  actually gets executed **before gdm  **is terminated, but **after the session applications where killed and gdm session was closed**, and that's the problem. 

I need to get this command executed before the active gdm session is terminated and all user running apps are killed...

Any hint anyone........... 

](*,)

---

