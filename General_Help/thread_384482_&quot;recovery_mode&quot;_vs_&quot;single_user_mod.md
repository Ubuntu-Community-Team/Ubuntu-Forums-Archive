---
title: "&quot;recovery mode&quot; vs &quot;single user mode&quot;"
date: 2007-03-14
forum: General Help
---

### Post by kitman420 on 2007-03-14
Lets pretend that I have an ubuntu 6.0 (kernel 2.6.15) system that is being built by NASA to be sent up into space. That is, whatever the runlevel of the computer, it needs to have ssh, sysklogd, and networking enabled so that I can talk to it.

Say i'm in runlevel 2, everything is fine, i have ssh, sysklogd and networking started. 

Now, something goes wrong and the system goes to runlevel 1. In runlevel 1, the system performs the actions dictated by the rc1.d directory: some daemons get killed and then /etc/init.d/single is called which kills remaining programs and starts /sbin/sulogin.  I modified my /etc/init.d/single script to start the necessary communications. It works.

Another scenario is if the system reboots and goes into "recovery mode" from the grub menu. In this state, it doesn't go to runlevel 1. It just runs all the scripts in the rcS.d directory. So essentially "recovery mode" and "single user mode" are different modes. At first glance, a quick fix would be to link /etc/init.d/single into the rcS.d directory. But, when the system is starting runlevel 2, it first calls everything in rcS.d and then everything in rc2.d and I can't have it going into single user mode in rc2.d

So, my question is, how can I direct the "recovery mode" to go into actual runlevel "1" and not runlevel "S" so that I can start the necessary communications. 

I guess I could just disable the recovery mode option in grub, but that is not the right solution. The system could still go into the recovery mode if the regular boot process fails.

Thanks, 

Dan

---

