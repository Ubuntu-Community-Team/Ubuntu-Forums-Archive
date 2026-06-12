---
title: "Ubuntu (Dapper) see's Ubuntu Live cd as blank CD-R"
date: 2007-04-05
forum: General Help
---

### Post by prophet9 on 2007-04-05
A little background (not much, cause you probably dont care :)  This is my second attempt in my life to install Linux onto my home PC.  The last time was several years ago and I tried several varieties (SuSe, Mandrake and Redhat I think) but i gave up because I really didn't know what I was doing.  Now I have a job where I use unix daily (HP-UX) so I'm alot more familiar, at least with the terminal.

I ran into an IRQ problem when I tired to run the Dapper live cd, which was fixed by adding the irqpoll option to the boot.  I installed w/o a hitch from there and my dual boot is working fine.  (Thankfully)

Now I'm trying to get my wireless card to work (no small feat there) but to do that i need access to the Ubuntu install cd.

**Now heres the rub, when I insert the Ubuntu Live cd into my drive, it shows up as either a blank cd-r or it shows up as a blank cd-r then disappears.  [COLOR="Red"]This happens with ANY cd I insert.[/COLOR]**

Any help would be appreciated.  My system is home built.  It's a Pentium D 2.66 with 4 gigs of ram (which only shows up at 3200MB but thats because of my Asus P5LD2 motherboard), a Hitachi DVD-ROM and a Samsung DVD burner, SB Live sound card, Linksys WMP11 wireless pci card (which I learned is actually a Broadcom BCM4303) and 2 SATA hard drives (a 500gig with Windows on it and a 160gig with Ubuntu on it)

Thanks

---

### Post by mssever on 2007-04-05
A couple of things: First, welcome to Linux! I've enjoyed Linux much more than HP-UX.

Why do you need the Ubuntu CD in order to setup wireless? Can you plug in to a regular net connection temporarily?

Despite that, the CD really should work. Since you're familiar with the terminal, check the output of ```
mount
``` after you insert the CD. If it shows up, cd to the CD's directory and see if you can see stuff that way (via the terminal).

Also, try manually mounting the CD via the command line. Post any error messages you get.

---

### Post by prophet9 on 2007-04-05
It's bizarre, I was able to manually mount the Ubuntu CD, but a blank cd-r still shows up on my dekstop whenever I enter it.  But at least it mounted.

Thanks for the help mssever.

---

