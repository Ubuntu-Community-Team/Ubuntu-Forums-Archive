---
title: "Gutsy randomly crashes"
date: 2007-11-01
forum: General Help
---

### Post by Phantom784 on 2007-11-01
After a few minutes of use, gutsy randomly freezes up on me.  ctrl-alt-backspace doesn't even work; the only way to get out is to use "alt+sysreq+reisub".  Anyone know what's wrong? here are some specs on my pc (in case that helps).  i previously used feisty on the exact same machine and i never had this problem.

dual core amd 64 processer (1.9ghz)  (however, i'm using the i386 install)
1 ghz ram
nvidia 7300 graphics card (using the driver as installed by envy, but i had the same problem with the normal restricted driver)
20gig drive form main install plus a 100gig drive for data

---

### Post by marx2k on 2007-11-01
> **Phantom784 said:**
> After a few minutes of use, gutsy randomly freezes up on me.  ctrl-alt-backspace doesn't even work; the only way to get out is to use "alt+sysreq+reisub".  Anyone know what's wrong? here are some specs on my pc (in case that helps).  i previously used feisty on the exact same machine and i never had this problem.

dual core amd 64 processer (1.9ghz)  (however, i'm using the i386 install)
1 ghz ram
nvidia 7300 graphics card (using the driver as installed by envy, but i had the same problem with the normal restricted driver)
20gig drive form main install plus a 100gig drive for data

I've had these sorts of issues, though in my case it seemed to be SAMBA trying to mount remote shares that were not shared at the time.  I am not SURE if that's what it was, but that seems to have fixed it.  Of course for you, it's probably something different :)

---

### Post by Crafty Kisses on 2007-11-01
> **Phantom784 said:**
> After a few minutes of use, gutsy randomly freezes up on me.  ctrl-alt-backspace doesn't even work; the only way to get out is to use "alt+sysreq+reisub".  Anyone know what's wrong? here are some specs on my pc (in case that helps).  i previously used feisty on the exact same machine and i never had this problem.

dual core amd 64 processer (1.9ghz)  (however, i'm using the i386 install)
1 ghz ram
nvidia 7300 graphics card (using the driver as installed by envy, but i had the same problem with the normal restricted driver)
20gig drive form main install plus a 100gig drive for data

Check your System Monitor, to see if anything is using up a lot of resources, and possibly causing a crash, or download gkrellm, that'll tell you how much CPU% is in use.

---

### Post by Phantom784 on 2007-11-04
I opened up system monitor to see if any process or anything was causing it to crash, but all the processes were normal, and both cpu usage and ram stayed at reasonable levels, not even showing any sort of spikes when the computer froze up again.

---

### Post by nick_h on 2007-11-04
Do you have Visual Effects enabled?

---

### Post by Phantom784 on 2007-11-04
i do.  could that be the problem?

---

### Post by Phantom784 on 2007-11-04
Turning visual effects off seams to have helped, I have an uptime of 23 minutes as of this posting! (w00t)

i'm still having a problem, however, with my lcd screen randomly going blank for a few seconds (which it always does when i change screen resolution, but i'm not changing resolution).  i have a crt attached also (dual monitor) and it isn't affected.  also, i didn't notice anything going out of control on my system monitor when this happened.  this is a brand new problem for me that i never saw on feisty or before.

edit:  spoke too soon, computer crashed, same ways as before, a few minutes after i posted it.  again, no spike on the system monitor.  took longer with visual effects off, but there's still a problem.  i'd think it was a memory leak of some sort, except i don't see memory usage going up on the system monitor, so i dunno.

---

### Post by Phantom784 on 2007-11-11
I've determined that my problem is most likely because of the regression in the binary nvidia driver that causes random lockups with 7000 series GPUs and SMP (both of which I have). I reinstalled and didn't install the restricted driver, and everything is working fine.  However, I'd still like to be able to use the restricted driver.  What's the best way to install the old (.09) nvidia driver?

---

