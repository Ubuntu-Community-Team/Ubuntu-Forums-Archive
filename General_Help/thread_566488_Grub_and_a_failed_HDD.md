---
title: "Grub and a failed HDD"
date: 2007-10-03
forum: General Help
---

### Post by webagent01 on 2007-10-03
So I was working in Windows and my computer quit. Poof. Not the BSD just everything quit except the mouse. So I restarted it. Grub came up (I'm running Ubuntu 6.10). I chose windows and hit enter. Next thing I get is a error 27(I think it was 27) disk read error. So my computer Guru says I've got a blown HDD. And no, Ubuntu won't load either, same message. This isn't that big a deal because I had my 60gig crammed full and needed more room anyway. I also had all of my important stuff backed up as well. So, I got a new HDD and am getting ready to start over. My question is, why do I see Grub and is this going to give me  a problem since I will be installing Win XP first? I was reading through the Grub info and it seems that it resides in the boot sector of the HDD. Does some of it reside somewhere else and allow it to show even if the HDD isn't spinning? Does this mean that the HDD is spinning but there is some other problem? I would really like to know if/how this will affect reinstalling Window$.

Stephen

---

### Post by dabl on 2007-10-03
"Blown" is probably not the right mental picture -- "slower than spec" may be better.

It's not an unusual end to a hard drive's life to have the bearings begin slowly to fail, and the result is the spin-up time exceeds a specified maximum that is self-tested upon startup.  On trick that sometimes works is to let it sit there spinning with the error message up for 5 minutes, then push your "reset" button and sometimes it is spinning fast enough to boot at that point.

You'll want to install your new hard drive as the new "first" drive, either physically on the IDE cable or else in BIOS, so when you install Windows it will naturally look like "C:".  If needed, just disconnect the old drive for this purpose.

There's a reasonable chance that the old drive, when configured as a "second" or "slave" drive, still functions well enough that a running OS will be able to copy data off of it onto your new drive.

HTH!  :popcorn:

---

### Post by webagent01 on 2007-10-03
It's a laptop. No second drove option. I will give that a try but I don't think that is the problem. Thanks

Stephen

---

### Post by dabl on 2007-10-03
Bummer.

Well, if the controller circuitry actually broke, which is the other likelihood, then it's probably a paperweight, even if it spins.  :(

You can pay $$ to have the data recovered, but you can't get to it yourself through a blown controller.  :(

---

### Post by webagent01 on 2007-10-03
So, no idea about why Grub is displaying its menu or whether that is going to cause a problem?

---

### Post by webagent01 on 2007-10-03
I restarted my computer to try some ancient tricks that someone said might work. This time I listened closely to my HDD. Spins up? Check... Seeking? Check... Hmmm, what is that noise??? Sounds kind of like a cd player where the head can't decide what to read because the disk is scratched... So, apparently it can read the boot sector enough to load grub but nothing more???

---

