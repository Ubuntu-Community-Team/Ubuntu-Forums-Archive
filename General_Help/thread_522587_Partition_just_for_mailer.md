---
title: "Partition just for mailer"
date: 2007-08-10
forum: General Help
---

### Post by jonathonblake on 2007-08-10
All

I'd like to put my MTA, and email client in their own partition.  One used just for the mailer.   I couldn't find any pointers to doing that.  :(  

Can somebody point me in the right direction? 

The rational for doing this, is to minimize the system slowdown that occurs when email is sent, or received. (I'd get a used box just for email, but I don't have the space on my desk for another keyboard and mouse. The only thing that the KVM switches I've seen/used have worked for, is the monitor.If I could restart the keyboard driver, without a keyboard, that wouldn't be an issue.)

xan

jonathon

---

### Post by olejorgen on 2007-08-10
If you need to share mouse / keyboard you should look into **synergy** (Not sure how it'll work if you only have one monitor)

I'm not sure I understand what kind of slowdown you're talking about? Do you have a very old PC?

Do you want the email partition to be on your main computer?

---

### Post by jonathonblake on 2007-08-10
[QUOTE=olejorgen]If you need to share mouse / keyboard you should look into **synergy** (Not sure how it'll work if you only have one monitor)[/quote]

I wasn't aware of Synergy.   KVM switches will switch monitors correctly.  
I'll set it up and see how it works on my existing Win2K & Linux box.  I don't know how many times I've used the wrong keyboard, or mouse, because I've forgotten which keyboard was with which computer.

> 
I'm not sure I understand what kind of slowdown you're talking about?

CPU is at 100%. Everything "freezes" up till mail has been retrieved/sent.   

>  Do you have a very old PC?

My system is about a year old.  


> Do you want the email partition to be on your main computer?

If I am going to have email on my main system, then I want to try it on a partition of its own.  See if that reduces/eliminates the system freeze.  If that doesn't work, I'll get a system just for email.

xan

jonathon

---

### Post by olejorgen on 2007-08-11
> CPU is at 100%. Everything "freezes" up till mail has been retrieved/sent.
That can't be normal (?) Out of my scope though.

To put email on its own partition you I think you should edit **/etc/fstab** such that the new partition is mounted on /<path-to-email-archive>

Then copy all your existing email to the new partition.

Think that should do it, but it mught have some flaws. (I'm not a guru :) )

---

