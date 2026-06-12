---
title: "Move hard drive to new system without reinstalling?"
date: 2006-10-24
forum: General Help
---

### Post by pumpkinpapa on 2006-10-24
I'm using 6.0.6 and I want to move the hard drive from one system which is failing to another working system without reinstalling. Can I do this?

Or could I simply install over itself and keep all my changes intact?

I seem to remember doing this with Caldera back 7 years ago but I may be mistaken.

I want to do this because my burner died and I have no way to back up my data without making a new partition and saving the data there before reinstalling.

---

### Post by aysiu on 2006-10-24
Have you considered PartImage?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by ~LoKe on 2006-10-24
You could mount that partition on a different computer, but not as a primary drive; the hardware is probably different and it would bitch and complain.

---

### Post by pumpkinpapa on 2006-10-24
Thanks aysiu and ~Loke, the old system is an AMD Duron and the new is an Intel P4 (well newish actually, as the Duron has DDR and the P4 has SDRAM but the Intel doesn't lock up as much). 

PartImage looks great, I'll be sure to use it, it looks like a free Ghost tool but more flexible.

Bitch and complain isn't so bad, much rather have that then HAL errors :)

---

### Post by x64Jimbo on 2006-10-25
Do not just move the hard disk or image the drive. Those options are only for when you are moving it to an IDENTICAL system. You WILL have big problems if you just transfer the files over. For a stable system, you will NEED a fresh install. I'm not kidding.

---

### Post by sefs on 2006-10-25
Not recommending this...

But back in the Breezy days I had my HD in an intel machine on an intel board.  I was too lazy to back up or image.  So I plucked the drive out and put it in an amd/msi machine and booted.  It picked up all the new hardware ect, and I am still using it today.  I've also upgraded this same drive to Dapper since then. That was like 3-5 months ago though.  I still see no ill side effects.  I guess I was lucky.

---

### Post by J4DED on 2006-11-05
I have a question regarding this, does ubuntu automagically select a different kernel if the hard drive is moved to a system with a different cpu?

I have Edgey running on a laptop without a cdrom - in order to install it I had to use a different laptop. I installed it on a P4 3.2GHz HT but am running it on a P3 600MHz.

Does ubuntu have different kernel versions for these two cpus? And if so would I see gains if I manually changed it to a different version?

---

### Post by x64Jimbo on 2006-11-06
There are different kernels that you should use for those CPUs, but you probably used the generic i386 installer (which works, albeit not optimally, on almost everything) on the P4, and it continued to work when you moved the HDD. Ubuntu doesn't automatically switch kernels.

---

### Post by handy on 2006-11-07
I ***think*** that Edgy only has one kernel, one size fits all kinda thing!

I have also heard of others just moving the boot partition (& whatever other partitions that drive may include) to a new machine & carrying on...?

I'll have to try it, it's the only way to know. :)

I would expect to have to make xorg.conf adjustments at least?

---

### Post by J4DED on 2006-11-07
After reconfiguring Xorg I was up and running. I was wondering if I would be getting better performance with a different kernel.

---

### Post by handy on 2006-11-07
> **J4DED said:**
> After reconfiguring Xorg I was up and running. I was wondering if I would be getting better performance with a different kernel.

Apparently **not** if you are using Edgy!

I could be wrong, but I think that the reason that Linux can be moved from computer to computer is that it sets up a lot of the hardware every time it boots up.  So you are *probably* on the best kernel setup already since you are using Edgy it may very well have auto configured the kernel for you.

If anyone has hard knowledge about this, please post here?

---

### Post by J4DED on 2006-11-07
What I find confusing then is that xorg in 6.06 detected some hardware better than 6.10 - I had to guess at settings and eventually get it right.

I wanted to stay in 6.06 but ironically my xircom networking card wasn't detected but it was in 6.10

I am finding that 6.06 was more stable as well, firefox and flock are always crashing on 6.10 but without the network card drivers it is unusable.

So I guess the newer kernel in edgy has more drivers built in?

---

