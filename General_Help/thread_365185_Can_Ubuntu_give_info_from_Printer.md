---
title: "Can Ubuntu give info from Printer?"
date: 2007-02-19
forum: General Help
---

### Post by whitefort on 2007-02-19
Hi,

Over the weekend, one of the cartridges in my Epson printer ran out of ink.  

This made me aware of an apparent shortcoming with Ubuntu (I say 'apparent' because I'm hoping someone will show me that I'm just missing something. I'm still a newbie, so please don't be ***too*** hard on me!)

The problem is that there are 4 cartridges in the printer.  Unbuntu gives me no clue as to which one has run out.  In fact, I had to disconnect the printer, take it to a windows machine, and look at the windows printer info to find out which cartridge needed to be replaced.

Surely there's a way to do this in Ubuntu?  Otherwise I'm going to have to keep windows installed just to replace printer cartridges!

Thanks!

---

### Post by nikhilk on 2007-02-19
I found this [link]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") from the Epson website. I have no idea about the features provided by this driver or even if it works for the printer model you have. You can try this (prefarably on a test machine) and see if it works for you.

---

### Post by bmt on 2007-02-19
There is escputil, which is available in the Ubuntu repositories.  This is a command line utility and has to be run as root (i.e., sudo escputil) in order to talk to the printer port at a raw level.  It also needs some command line options so it knows where the printer is -- inconvenient rather than difficult.

There are several gui front ends available (Google 'escputil gui'), some nicer looking than others -- take your pick. They all need to be run as root, for the reasons given above, so they're not quite as friendly as the Windows utility.  At least it's not necessary to move the printer. ;-)

Edit to say: mtink is also in the repositories, so it's easy to find and install.  Then is just a matter of 'sudo mtink' for a graphical representation.  You still need to have escputil installed as well.

---

### Post by whitefort on 2007-02-19
Thanks, guys.

it turns out that Mtink is EXACTLY what I was looking for.

Now I'm a happy Ubuntu user again!

---

