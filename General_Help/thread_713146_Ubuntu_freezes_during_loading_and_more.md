---
title: "Ubuntu freezes during loading and more"
date: 2008-03-02
forum: General Help
---

### Post by percussionhall on 2008-03-02
Hello all,

I posted on another thread that I thought I had a similar problem, but I guess I dont, so here is my situation:

I dual booted Windows XP and Linux on my HP Pavilion  a111On (that is the name ON the actuall computer shell).  It took me a while to figure out how to install it because I didn't want to lose my memory.  But then eventually after a few problems (and ending up using the alternate CD and ide=nodma to install), I got it installed on my computer, and I got my computer to boot to the GRUB menu thingy.  

By the way, on the install, I skipped the steps where you find the HTTP Proxy because I have no clue what that is, and the step where you "configure your network with DCHP".  It loaded that bar, and then said that it failed to configure my network with DCHP every time I tried. Just adding this in case it contributes to my problem.

OK, on the GRUB menu, it has 5 choices:

-Ubuntu
-Ubuntu (recovery mode)
-Ubuntu (memory test) (if I remember correctly)
-Windows ../../../XP  (<--I don't remember...the others were things like 2000, NT, etc...)
-Windows XP

The only one that boots into a functioning OS is the last one, which works fine.  The second to last one I think runs a windows xp recovery.  The third one I tested and it comes up with what I guess is a memory analyzing screen.  I have never gotten through all of that test because I am impatient :). OK here to my problem areas:

On the first option, just regular Ubuntu, it gets to the loading screen and then freezes at probably about 30%, it just fills up three of the little sections. That is basically my problem with that.

On the second option, a few things have happened to it.  The first time I chose that one, it was going normally, and then it got to this screen where text is flashing up the screen, and, though I can't read it, it seems to be all the same thing, except on the left of every line, there are numbers going by. They look something like:

{[64.13413457547]} [and then there are a bunch of text flying by over here]

I thought that it was doing something since it was moving, so I left it for a few hours, and when I got back, it was still going and the number was something like 16000. :confused: This has happened twice, and the second time I didn't let it run for nearly as long.

My other problem with the recovery mode option is that it gets part of the way through the normal stuff and just stops.  I'm pretty sure that it's frozen, but I don't really know.

I have tried editing the Kernel menu thing. I went there and changed "root=UUID-###..."  to "root=/dev/*d*" (I replaced *d* with sda3 because that is what partition the installer disk said my linux was installed on.  I still had the same problem

Thank you for all the help that you can give.  If you need more info to help, please tell me how to get that info because I don't know how to type in commands and stuff.

---

### Post by percussionhall on 2008-03-02
I hope people can help me with this.  I have tried looking places and have not found a solid solution.

Thanks

---

### Post by percussionhall on 2008-03-03
THANKS for all of your help, guys.  I am really attracted to Ubuntu after all of this support I've recieved.

xP

---

