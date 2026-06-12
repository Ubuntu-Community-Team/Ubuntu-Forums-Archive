---
title: "partitioning question"
date: 2008-07-08
forum: General Help
---

### Post by aerospace1028 on 2008-07-08
[LEFT]greetings,
Just a little background:  I've been experimenting with Ubuntu 7.10 for a few months now on a test machine.  I'm getting ready to install Ubuntu on my every day machine.  I'm planning to download Ubuntu 8.04 and duel boot with WindowsXP.  

I have decided I can afford to use 10 GB for the Ubuntu partition.  I want a root (/), a home (/home), and a swap partition.  What is the best sizing for this set up?

My laptop that I am installing to has 1.5 GB ram, with a maximum capacity of 2 GB.  I read somewhere that the limit for swap is 2 GB: should I just install 2 GB sswap, so when I upgrade my ram, I'm already at the max swap?  Or do I need 2 GB swap ever?  I am visually impaired and use orca: I don't do any graphics, video, or sound editing/production: so would the physical ram + a smaller (say 1 GB) swap be sufficient?

On my test machine, I gave 8 GB each to root (/) and home (/home).  Running df --human-readable says that / uses 3.4 GB and /home uses < 1 GB.  I remember reading that ext3 (the file system used by Ubuntu) needs a little extra space for security reasons.  What is  good ratio of partition sies for / and /home?

based off the usage reported by df on my test machine, I was planning on:
/ = 6 GB
/home = 2 GB
swap = 2 GB

Thank you in advance for any assistance or advice you might have.[/LEFT]

---

### Post by Elfy on 2008-07-08
Do you hibernate the laptop - if you do then swap should equal ram, if not then I would suggest that 1Gb would be more than sufficient. I have a smaller RAM than you and only use the swap when I use a virtual machine.

So, assuming you don't need to hibernate, then I would

/ - 6Gb
/home  - remainder
swap  - 750Mb

Also, I don't know if I would be bothering with a seperate home as it is likely that you could easily copy your home onto a couple of discs if the need arose.

You would then be in a position where your /home could grow as necessary and the / wouldn't be as constrained.

So that'll be my pennyworth :)

---

### Post by enchesss on 2008-07-08
what is the total size of your hard drive?

10gb should work but it seems small for everyday use!

Using the default size for swap partitions of best.

If you are doing a new windows installation as well then you should give windows 10gb and isntall this first

then install ubuntu and let it use the guided partitioning of the largest available space.

---

### Post by Elfy on 2008-07-08
> Using the default size for swap partitions of best.I would disagree with that if you have plenty of RAM and no intention of hibernating, it would be a waste of limited disk space.

But I'd agree with the 10Gb thought.

---

### Post by aerospace1028 on 2008-07-08
> **enchesss said:**
> what is the total size of your hard drive?

10gb should work but it seems small for everyday use!

Using the default size for swap partitions of best.

If you are doing a new windows installation as well then you should give windows 10gb and isntall this first

then install ubuntu and let it use the guided partitioning of the largest available space.

I'm already using the machine with Windows.  I'm more comfortable using the Ubuntu CD to resize the windows partition (after backing everything up first) an putting ubuntu in the freed space.  


As far as 10 GB being too small, it's what I'm comfortable sacraficing at the moment.  As I get more familiar with Ubuntu and use it more, I can consider expanding the partitions when they get a little crowded.

---

### Post by Elfy on 2008-07-08
I'd go with my first thought - decide on swap in relation to hibernate.

When you come to resize make sure that xp has been defragged a couple of times at least and also that it was shutdown cleanly.

Of course if it's only 32bit it would be pointless overdoing the swap as it mightn't all get recognised.

---

### Post by aerospace1028 on 2008-07-08
Thank you,
The hybernation rule helps out.  I don't plan to hybernate, so I won't need that much swap.

I'll consider your advice about just one partition instead of breaking off /home.  I read about using /home to preserve the configuration files over upgrades, but I never thought to just restore /home from back-ups.

Thank you:-)



> **forestpixie said:**
> Do you hibernate the laptop - if you do then swap should equal ram, if not then I would suggest that 1Gb would be more than sufficient. I have a smaller RAM than you and only use the swap when I use a virtual machine.

So, assuming you don't need to hibernate, then I would

/ - 6Gb
/home  - remainder
swap  - 750Mb

Also, I don't know if I would be bothering with a seperate home as it is likely that you could easily copy your home onto a couple of discs if the need arose.

You would then be in a position where your /home could grow as necessary and the / wouldn't be as constrained.

So that'll be my pennyworth :)

---

### Post by Elfy on 2008-07-08
Yea - if later you decide to increase the partition size then you could migrate your home from within / to a partition of it's own then, in the meantime I'd leave it inside / personally.

So if you don't hibernate then I really see no need for you to have much more than that as swap.

Good luck with it

---

