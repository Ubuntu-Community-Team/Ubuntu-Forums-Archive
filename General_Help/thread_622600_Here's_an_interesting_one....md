---
title: "Here's an interesting one..."
date: 2007-11-24
forum: General Help
---

### Post by derekr44 on 2007-11-24
So my father's Windows install blue-screened (suprise) and I wasn't able to fix the issue.  I booted Ubuntu Live and was able to get his files onto my flash drive.

Now comes the fun part.

He wants to try Ubuntu on it.  The problem is that it's an old Gateway Solo 2550.  It's a P3 550 with 128mb RAM and a 6gb drive... and the CD drive is busted physically.  There is no ethernet port on it.

So I had the thought of putting his hard drive in my laptop and installing Ubuntu, which I did.  I went in to xorg and switched the graphic driver to vesa and set the resolution to 800x600.  I swapped the drive back into his laptop and booted up.  When I booted, I saw GRUB and then I saw the Ubuntu splash screen.  Then a black screen.  Assuming that it was a resolution issue, I hit Ctrl+Alt+F2 to try and bring up the CLI but nothing happened there either.

I know this is a resolution problem because I can swap the drive back into my laptop and it boots just fine.  How can I get this to work on his laptop?

[Specs on the Solo 2550 are here](http://support.gateway.com/s/Mobile/Solo_Series/P2550/p255044.shtml)

---

### Post by Tundro Walker on 2007-11-25
1) I think this thread should get moved to a more appropriate forum.  Not that I hate this thread...it's just that there's more appropriate threads for problem resolution.

2) When Ubuntu installs, doesn't it spec your machine and hard-set some variables?  That might be dogging things up.  Of course, I say that, but then one of the "speedy bootup" tweaks is to get GRUB to -profile your system.  But that may be talking about 2 different animals...what GRUB needs to boot might be different then what Ubuntu has written down somewhere.

A friend of mine and I swapped out an old MS WinXP hard drive into another computer, and it booted up fine.  The Linux kernal carries all the drivers needed (theoretically, depending on modules its built with), so maybe it's set to use a certain kernal on your machine when it needs to use a different one on your Dad's?

Seriously, it's like $50 for a new CD drive.  Just get one, and install using a distro disk.  I take it your Dad's comp is so old it doesn't do USB very well (might not even have ports?)  If it did, you could try tossing the distro disk on a USB stick (or like an iPod's storage drive), and try booting the comp from USB...might be able to use the USB like a distro disk.

Still think you should just pop for a CD drive.  Heck, go to an old comp store...they might sell you one for $20.

---

### Post by TeaSwigger on 2007-11-25
That's not enough RAM for ubuntu, kubuntu or xubuntu. Really. It just might work tolerably with Fluxbuntu or a "bare bones install" if one is conservative in what they add on. A lighter weight distro could get it moving briskly though. 

Generally it seems that installing on one box and moving the hd to another box with different hardware won't be successful unless you know what to do. And I echo the sentiment of fixing the CD drive if you can afford it and if the rest of the unit is working ok. :)

---

### Post by der_joachim on 2007-11-25
> **TeaSwigger said:**
> That's not enough RAM for ubuntu, kubuntu or xubuntu. Really. It just might work tolerably with Fluxbuntu or a "bare bones install" if one is conservative in what they add on. A lighter weight distro could get it moving briskly though. 

Generally it seems that installing on one box and moving the hd to another box with different hardware won't be successful unless you know what to do. And I echo the sentiment of fixing the CD drive if you can afford it and if the rest of the unit is working ok. :)

I have an ancient laptop (P3, 700Mhz with 128MB ram) with Xubuntu which is actually quite workable. Admitted, it is not such a speed monster as my main PC, but it runs way better than when it had XP on it (which is not so strange  ;)). 

However, I second the remark that the OP should probably be getting Puppy or DSL and do away with all the tweaks I had to do. ;)

---

