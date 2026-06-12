---
title: "Encoding DVD (K9copy) totally kills Firefox"
date: 2008-06-12
forum: General Help
---

### Post by coloradoguy on 2008-06-12
Hey Guys -

This is a pretty strange problem, but I figured I would see if anyone had any ideas because.. well - I'm all out.

I have a nice new Dual Core system (Dual Core 2.4 ghz, 2GB Memory, etc) and am having some problems with encoding DVD's on my Ubuntu install. 

When K9Copy is running and doing its encoding (taking a larger DVD and making it small) firefox constantly goes grey and becomes unusable. Eventually it comes back and I can maybe use it for a second or two but then it disables again.

Now a few strange things:
1) This does not happen when I boot from Ubuntu LiveCD
2) This does not happen on my Linux Mint install

What I have tried so far are these things (and none of them have helped):
1) Downgraded firefox to 2.0 and removed all addons
2) Other DVD encoding applications (including dvdshrink through wine)
3) Disabling compiz-fusion
4) Removing my nvidea graphics card
5) Removing flash, java, etc


The logical options seem to be to switch over to Mint or just reinstall Ubuntu but it seems silly to reinstall for this. Does anyone have any ideas???? I'm really perplexed!

Thanks in advance!


**Update
1) While the DVD is encoding I watch the CPU usage, it stays low, usually well below 50% total utilization
2) Other system applications might slow down a little, but nothing freezes or goes grey like Firefox

---

### Post by Bizzako on 2009-01-01
I am have the same problem, except it extends to other apps as well.

When I use k9copy (version 2.0.2 on Intrepid), it has the effect of rendering my computer unusable for the next 20 minutes (while I am encoding, it takes apps more than a minute to open, then constantly cycles between regular and greyed out). Does anybody know how to prevent it from using my system's complete resources so I am able to perform other tasks?  I have tried lower it's priority in the system monitor, but that doesn't seem to help. I would be very grateful if anyone has any ideas.

Thanks,
Bizzako

---

### Post by daev64 on 2009-02-21
I also have issues, albeit different ones, with k9copy. I can keep multi tasking with no issues (FF works just fine), but randomly compiz takes a big dump, moves all of my open apps to a single desktop and drops me to the default 2 desktops with no keyboard shortcutting between them. This seems to be followed by failed encoding, ie. k9copy will eventually error out or finish and leave me with a corrupted rip.

edit: 2.4Ghz AMD quad 4GB 1066 RAM, intrepid, k9copy 2.0.2

---

### Post by csrobins on 2009-08-10
I'm on a laptop with a Core 2 Duo 1.8GHz and 2GB RAM. I'm having the same problem with Firefox graying out here in Jaunty. But it happened while using DVDstyler v1.7.2 to burn a DVD from a couple of mpg files. I wonder if it might have something to do with the hard drive instead of the processor. The access light on my laptop was solid while it was encoding and the CPU hardly went above 20%. 

This is only the second time I've tried to burn a DVD. The first time the computer slowed down but not as bad (firefox never froze like it did the second time), but I was saving the tmp image of the DVD on a different partition (same physical drive though). Unfortunately I ran out of free space and hit and error. That's why I switched partitions. Firefox is on my root partition, but my FF profile and the tmp image were both on the same non-root partition.

The system performance definitely took a hit while I was initially encoding the videos with ffmpeg, but that's expected with the CPU hovering around 98%. Doesn't make sense how it could be worse when the CPU is only at 20% though.

Any ideas?

---

### Post by mellery on 2009-12-01
I've just started seeing this problem too since upgrading to karmic

---

