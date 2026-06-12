---
title: "hardy cpu peaks"
date: 2008-05-16
forum: General Help
---

### Post by bro on 2008-05-16
Since I switched to Hardy my cpu peaks for several seconds from time to time (say every 10 minutes or so). The mouse and all other programs become unresponsive. When playing music or video this goes gagagagagagagagagagaga. It is quite horrible. 
A solution? 

p.s. I'm using hardy 32-bit but the 64-bit had the same. I've got a proprietary-drivers-free system. Could it be intel-drivers? I really don't know where to go with this - it does make me feel ashamed to use ubuntu LTS.

---

### Post by ibuclaw on 2008-05-16
First, I'd enable all proprietary drivers in the restricted drivers app. "System>Administration>Hardware Drivers"

We may all prefer the views and opinions of open-source, but that shouldn't mean that we must all be Richard Stallman!

If you have any drivers to install, install them and reboot your PC.

If it happens again, open up the terminal and type in:
```
dmesg | tail
```
And copy and paste the output of it in your next post.

Also, open up the system monitor "**System>Administration>System Monitor**" and look for any spikes in the CPU and for any resource hungry apps running.

[EDIT]
I would call every ten minutes rather frequent, and it should be looked at immediately.

If it is hourly, there could be a resource hungry cronjob running, and if there is, that needs disabling (or pushed to a weekly or monthly task).

Else, every other hour would be generally acceptable way of putting "from time to time".

Regards
Iain

---

### Post by bro on 2008-05-17
Thanks for the advice. I'd didn't manage to reproduce so far as I was on cable instead of lan for a while... maybe that is the solution/problem. 
Would you know a (simple) way of downgrading my wireless driver (intel, it says  iwl4965 in connection information). [I found out that I am not alone by the way.]("http://ubuntuforums.org/showthread.php?t=794170") So maybe continue the discussion overthere.

---

### Post by bro on 2008-05-18
tinivole, if you have clue, someone produced the output you requested, would you be so kind to take a look at it here? 
[http://ubuntuforums.org/showthread.php?p=4986395]("http://ubuntuforums.org/showthread.php?p=4986395")

And share your wisdom? (if any)

---

