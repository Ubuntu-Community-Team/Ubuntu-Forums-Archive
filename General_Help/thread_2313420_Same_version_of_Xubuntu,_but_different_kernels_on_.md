---
title: "Same version of Xubuntu, but different kernels on different computers?"
date: 2016-02-12
forum: General Help
---

### Post by Azdour on 2016-02-12
Hi,

I have two computers with Xubuntu 14.04 installed and up to date - the update manager is telling me they are up to date.

By running 'uname -a' I see the following differences:

Computer 1: 3.16.0-60-generic #80~14.04.1-Ubuntu SMP Wed Jan 20 13:37:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Computer 2: 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Does computer 2 have an older kernel because it is an older computer and newer kernels do not support it?  Just wondering why the kernels are not the same.

Thanks.

---

### Post by Nuno_Abreu on 2016-02-12
Not necessarily - probably you just upgraded your kernel in the first computer or even downgraded on the second one.
It doesn't hurt to try the most up to date kernel - if it does not work, boot from the previous kernel you have before on the Advanced tab on GRUB.

If you have any doubts, don't hesitate!

---

### Post by Azdour on 2016-02-12
Thanks for the quick reply.

I've only ever used the update manager and have never down graded the kernel that I am aware of.

As I understand it the Update Manager should offer the latest kernel.  It has been on computer 1 but nothing on computer 2 for some time.

---

### Post by Nuno_Abreu on 2016-02-12
It depends. Do you actually use PPAs, for example? Sometimes programs need a specific version of the computer, older or not (it's rare, though). Also, do you happen to use some "bleeding edge" repository like **xorg-edgers **for some speed or compatibility?: [http://bit.ly/1TgcvVp](http://bit.ly/1TgcvVp)

It shouldn't be a problem, anyway. What's strange is that they were compiled at basically the same time - that's what's intriguing me!

Do you happen to have some instability?

---

### Post by buzzingrobot on 2016-02-12
The 14.04 LTS release has received 3 "Hardware Enablement" upgrades ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack)]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") since its initial release. (And a fourth is due next week.)  These upgrades add a newer kernel and newer video stack components.  

All 4 install images remain available:  14.04, and then 14.04.01 through 14.04.03.

So, depending on when you installed both systems, and which installation images you used, this could easily account for the different kernel versions.

You'll see on that wiki that you can apply these upgrade manually, if you wish.  The usual caveats apply:  If you have no issues with the system currently, the safest route is avoiding change.

---

### Post by vasa1 on 2016-02-12
> **Azdour said:**
> Hi,

I have two computers with Xubuntu 14.04 installed and up to date - the update manager is telling me they are up to date.

By running 'uname -a' I see the following differences:

Computer 1: 3.16.0-60-generic #80~14.04.1-Ubuntu SMP Wed Jan 20 13:37:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Computer 2: 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Does computer 2 have an older kernel because it is an older computer and newer kernels do not support it?  Just wondering why the kernels are not the same.

Thanks.
See 
[http://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe](http://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe)
and
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

There's nothing wrong with either of your computers, AFAICT!

oops! Ninja'ed

---

### Post by Nuno_Abreu on 2016-02-12
> **buzzingrobot said:**
> The 14.04 LTS release has received 3 "Hardware Enablement" upgrades ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack)]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") since its initial release. (And a fourth is due next week.)  These upgrades add a newer kernel and newer video stack components.  

All 4 install images remain available:  14.04, and then 14.04.01 through 14.04.03.

So, depending on when you installed both systems, and which installation images you used, this could easily account for the different kernel versions.

You'll see on that wiki that you can apply these upgrade manually, if you wish.  The usual caveats apply:  If you have no issues with the system currently, the safest route is avoiding change.

And is it normal that they were compiled at the same time? It just seems odd to me!

---

### Post by buzzingrobot on 2016-02-12
You'd need to check the specifics of what upgrades were released when, but there's nothing to prevent an update to 3.13 from being built on the same day as the 3.16 version. The dates indicated that's what happened.

---

### Post by Azdour on 2016-02-15
> **buzzingrobot said:**
> The 14.04 LTS release has received 3 "Hardware Enablement" upgrades ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack)]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") since its initial release. (And a fourth is due next week.)  These upgrades add a newer kernel and newer video stack components.  

All 4 install images remain available:  14.04, and then 14.04.01 through 14.04.03.

So, depending on when you installed both systems, and which installation images you used, this could easily account for the different kernel versions.

You'll see on that wiki that you can apply these upgrade manually, if you wish.  The usual caveats apply:  If you have no issues with the system currently, the safest route is avoiding change.

Thanks.  That makes sense as they were installed at different times.  Computer 2 is a DRBL server for several client machines. Chrome on those machines has a habit of semi-crashing and I wanted to rule out the kernel as a potential source of the problem as Chrome works well on Computer 1.

I think I will need to do more investigation and probably raise a new thread.

Thanks to everyone for their help.

---

### Post by sabina2 on 2016-02-15
3.13.0, 3.16.0 and 3.19.0 are still improved and updated by Canonical. 3.13 is installed by default in 14.04 and 14.04.1. 3.16 in 14.04.2 and 3.19 in 14.04.3.

The first will be supported till 2019 while the others will have to be upgraded when 4.4.0 will be released into the 16.04 LTS.

---

