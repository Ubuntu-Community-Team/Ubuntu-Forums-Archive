---
title: "Freshly Installing Ubuntu if I Dual boot."
date: 2007-04-30
forum: General Help
---

### Post by twistedbydesign on 2007-04-30
I apologize if this subject has already come up before...i searched high and low before deciding to post my own.
I dual boot Ubuntu and Windows xp. (I'd like to go totally Ubuntu but i need xp for a few things...at least for now)
When I first installed Ubuntu and really didn't know ANYTHING about Linux. So i pretty much trial and errored my way through it until i had a good handle on it. That said, I know that in all my curiosity and tinkering, i manged to add things i didn't need, and get rid of things that would be nice to have, and change various settings etc. 
My Ubuntu has also recently been having problems with CPU spikes (i posted another thread about this but was still unable to solve the problem).
So I've decided that it would be much easier for me and give me more peace of mind to just completely Re-install Ubuntu fresh. (i think i'm actually going to go back to Edgy which is what i started with before i updated to Feisty...at least for the time being)
I was just wondering how to go about doing that without messing up my windows partition. I wasnt sure if there was something special that needed to be done. So any advice or even a step by step guide would be very helpful and appreciated.
thanks!  :)

---

### Post by confused57 on 2007-04-30
> **twistedbydesign said:**
> I apologize if this subject has already come up before...i searched high and low before deciding to post my own.
I dual boot Ubuntu and Windows xp. (I'd like to go totally Ubuntu but i need xp for a few things...at least for now)
When I first installed Ubuntu and really didn't know ANYTHING about Linux. So i pretty much trial and errored my way through it until i had a good handle on it. That said, I know that in all my curiosity and tinkering, i manged to add things i didn't need, and get rid of things that would be nice to have, and change various settings etc. 
My Ubuntu has also recently been having problems with CPU spikes (i posted another thread about this but was still unable to solve the problem).
So I've decided that it would be much easier for me and give me more peace of mind to just completely Re-install Ubuntu fresh. (i think i'm actually going to go back to Edgy which is what i started with before i updated to Feisty...at least for the time being)
I was just wondering how to go about doing that without messing up my windows partition. I wasnt sure if there was something special that needed to be done. So any advice or even a step by step guide would be very helpful and appreciated.
thanks!  :)

Before you reinstall Edgy, I'd recommend that you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a handy tool to have & you'd be able to restore your Window's IPL code to the mbr, if you needed to...it can also boot Windows or Linux.

You should be able to install Edgy onto the current partitions that you have for Ubuntu...you'll need to select "Manual partitioning", format your root (/) partition ext3, set the mountpoint as (/), set the bootflag to "on" and for swap, format as swap & set mountpoint as swap.  Just make sure NOT to select to format your Window's partition.  Edgy should install directly to the partitions that you're already using for Feisty.

Don't hesitate to post back if you have any questions.

---

### Post by twistedbydesign on 2007-04-30
I actually just Downloaded Super Grub Disk.
After i posted this one i saw another thread where they mentioned it so i decided to get it (i figured it'd  be nice to have even if i didnt need it right away).
I'll let you know if i have any problems.
Thank you very much!!

---

### Post by twistedbydesign on 2007-05-01
OK, I have freshly installed, it worked like a charm
The only weird thing now is that on GRUB i have 2 identical windows XP choices....which really isnt a big deal..just odd lol.
Thanks Again!

---

