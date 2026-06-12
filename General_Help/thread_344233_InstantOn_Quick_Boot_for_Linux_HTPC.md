---
title: "InstantOn Quick Boot for Linux HTPC"
date: 2007-01-22
forum: General Help
---

### Post by Spleenboy on 2007-01-22
I am sure I am the 1000'th person to ask this, but have googled and cant find a straight answer. 
I use Ubunutu at work, and want to build a micro itx HTPC at home with all the usual suspects: MythTV etc. However, I would also like a super quick boot (or dual boot) so I can also use it like a normal CD/DVD player. I have seen various boot hacks to shorten boot times. I have also looked at Intervideos InstantOn, but this seems only to be an OEM product, and my Linux is not good enough to build my own from an existing OEM.
Does anyone know any solutions already out there?
Is there a super quick boot option in Ubuntu?
I would guess any car systems would want this as well.

Many Thanks
Spleenboy

---

### Post by mgmiller on 2007-03-09
There is something called the linux bios, which claims 3 seconds from power on to console.  Maybe this could be helpful.  You have to pick your motherboard carefully, though.

[http://linuxbios.org/index.php/Main_Page]("http://linuxbios.org/index.php/Main_Page")

---

### Post by Redeyes_Gambit on 2007-03-09
You could also try installing Ubuntu to a flash drive. The easiest way to do this is to use a CF (Compact Flash) card with an adapter that makes it look like a standard HDD to BIOS/Ubuntu. I actually have an Ubuntu server running off a CF in this configuration. Made things easy as pie.

Try: [http://www.mini-box.com/s.nl/sc.8/category.14/.f](http://www.mini-box.com/s.nl/sc.8/category.14/.f)

For the adapter. I personally got this one: 

[http://www.mini-box.com/s.nl/it.A/id.206/.f?sc=8&category=14](http://www.mini-box.com/s.nl/it.A/id.206/.f?sc=8&category=14)

because it has mounting holes the same as the bottom holes on a standard HDD and a jumper that can make it either master or slave. Then you will need a nice big, fast CF card. Newegg has a nice 4GB one that operates at 120x:

[http://www.newegg.com/Product/Product.asp?Item=N82E16820211047](http://www.newegg.com/Product/Product.asp?Item=N82E16820211047)

The benefit of a flash drive is that they have REALLY fast seek time (the time it takes a device to "get to" data.) The drawback is that a flash drive has a slower sustained transfer rate than a HDD, so transfers of big files will take longer.

---

### Post by nathanziarek on 2007-03-23
Don't flash drive have a pretty limited number of read/writes before they die?

I've thought about doing something like you've got, with a large hard drive for media and CF for the OS, but i figured I'd burn through the CF card too quickly...

---

### Post by Redeyes_Gambit on 2007-03-24
From what I've read on wikipedia most manufacturers guarantee a flash card for a million read/writes (I'm guessing per cluster.) I've been running Ubuntu server on a CF for about a month now, but not with heavy usage (staying off most of the time. It will be under a much heavier load now.) 

It has lasted through a few formats and having it filled to the brim and taken back. So far no troubles. I'll try and remember to come back here and post should it ever fail on me.

(edit):

Well, it's now 8 months later and the card is still going strong. The server stays on pretty much 24/7, though there isn't much activity on the CF. Let's see how it's doing another 8 months from now...

---

### Post by BoyOfDestiny on 2007-04-15
> **Redeyes_Gambit said:**
> From what I've read on wikipedia most manufacturers guarantee a flash card for a million read/writes (I'm guessing per cluster.) I've been running Ubuntu server on a CF for about a month now, but not with heavy usage (staying off most of the time. It will be under a much heavier load now.) 

It has lasted through a few formats and having it filled to the brim and taken back. So far no troubles. I'll try and remember to come back here and post should it ever fail on me.

I really want to try this out. I think an 8 gig would be plenty, since using ubuntu I've never exceeding using 5gig in /... 

Just set it to ext2 so it doesn't do any auto defragmenting or journailing or anything (seek time isn't effected by fragmentation on these drives...)

Should extend the life of the card a bit.

---

