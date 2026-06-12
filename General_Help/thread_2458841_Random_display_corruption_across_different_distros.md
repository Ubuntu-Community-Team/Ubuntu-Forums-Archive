---
title: "Random display corruption across different distros?"
date: 2021-03-04
forum: General Help
---

### Post by lowang2 on 2021-03-04
Hello, 

I've been experiencing random display corruption issues across 2 different distros. (Image of corruption is at the bottom of this post)

I switched over to Ubuntu 20.04 hoping it would solve things but the same thing happens.

Previous to this I was using Pop!OS 20.10 and 20.04. 

I've tried adding the "nomodeset" kernel boot parameter using these instructions:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing](https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing)

*(I removed it after the frame rate drastically dropped)*

I've also tried these instructions found here (though they're specific to Pop!OS?): 
[https://www.reddit.com/r/pop_os/comments/jq96nk/graphics_corruption_on_window_resize_pop_2004_and/gblp3lb/?utm_source=share&utm_medium=web2x&context=3](https://www.reddit.com/r/pop_os/comments/jq96nk/graphics_corruption_on_window_resize_pop_2004_and/gblp3lb/?utm_source=share&utm_medium=web2x&context=3) 

[I](They didn't work)

[/I]My system specs are as follows: 
HP ProBook 640 G1.RAM= 12GB, CPU= Intel I5-4300M, Graphics= Intel HD Graphics 4600 (HSW GT2), HDD= 256GB.

What seems to "help"/temporarily resolve it is to "lock" my screen. As soon as I click "Lock" the display corruption goes away and everything is normal, until the problem shows up again randomly.

If someone could help me solve this issue, that would be great as I really want to enjoy Linux without having to lock/unlock my screen every time this happens.

[ATTACH=CONFIG]288057[/ATTACH]

---

### Post by Swan_DB on 2021-03-05
I am probably wrong, but:

Did you use the same medium to install these operating systems, example: USB stick or CD disc?  Maybe it corrupted a file?  You could try using a different install method.

Then there is this, which seems unrelated to a point, but sort of related: [https://askubuntu.com/questions/1320264/problem-with-the-rendering-of-text-menus-and-icons](https://askubuntu.com/questions/1320264/problem-with-the-rendering-of-text-menus-and-icons)

Has that PC ever worked on a different OS, such as Windows, without the image corruption?  If not, maybe it's a hardware problem in that computer?

Again, I'm an idiot, and a noob, just trying to give some ideas.  Good luck, OP : )

---

### Post by lowang2 on 2021-03-05
> **Swan_DB said:**
> Has that PC ever worked on a different OS, such as Windows, without the image corruption?  If not, maybe it's a hardware problem in that computer?

Funny you should ask that. One of the reasons I switched to Linux was because Windows 10 was giving me issues (a fresh install too, not related to display issues though).

It might be a faulty hardware issue (as this computer is a "hand me down" and the keyboard is not working (water spill/dirt)) 
The half mini wifi card (Intel AC7260) seems like it might be going out ? It keeps making chirping noises when using Linux but not on Windows (on Windows 10 it had connectivity issues). 

I don't know what's going on with this computer, I think it might be time for a new one?

---

### Post by Swan_DB on 2021-03-05
> **lowang2 said:**
> Funny you should ask that. One of the reasons I switched to Linux was because Windows 10 was giving me issues (a fresh install too, not related to display issues though).

It might be a faulty hardware issue (as this computer is a "hand me down" and the keyboard is not working (water spill/dirt)) 
The half mini wifi card (Intel AC7260) seems like it might be going out ? It keeps making chirping noises when using Linux but not on Windows (on Windows 10 it had connectivity issues). 

I don't know what's going on with this computer, I think it might be time for a new one?

If you can afford it, probably just get a new computer; you can get a decently powered one for less than five hundred dollars, or cheaper if you buy a used one, but I wouldn't buy used unless it's from a shop with a return policy, or they let you test it for an hour or so, to make sure it works.
Wish I could help.  Good luck :guitar:

---

