---
title: "0 Swap partition...what are the side effects?"
date: 2006-07-12
forum: General Help
---

### Post by PapaWiskas on 2006-07-12
I noticed someone in another post mentioned that their swap partition had been set to 0.

That really intrigues me, because I wouldn't mind have some of that space back on my laptop.  But I am really clueless as to how to change that, and if I did, what would be the side effects of doing something like that?

So if someone could enlighten me that would be much appreciated.

Again my goal is for 2 things.

1.)  How or what program would be needed to resize my swap partition?
2.)  What disastrous consequences would I face if I did so?

I primarily use my PC for Internet surfing, email, once and awhile GAIM and DVD creations (ripping, encoding, burning etc...).

---

### Post by T700 on 2006-07-12
How much RAM do you have?  Unless you have a very large amount, I would not suggest doing this.  Even then, I'd still leave a small swap area.

Paul

---

### Post by PapaWiskas on 2006-07-12
I have 1 GB RAM.  When you say small amount, how small can a person go?  I have never really seen the SWAP partition being used according to my GDesklets display applet.

---

### Post by cptnapalm on 2006-07-12
Depends on the initial setup and what filesystem you are using and possibly where on the drive, physically, the swap partition is.

For example I have a 256 MB swap at the end of the disk and I use xfs for my filesystem.  All I would have to do, should I desire to get rid of the swap partition would be to turn swap off, then use gparted to redo the partitioning then grow the xfs filesystem to consume the remainder.  BUT, if my swap partition was at physically before my xfs partition, the grow thing would not work.

What happens if you turn off swap?  Depends on how much ram you have.  If you have copious amounts, then most likely your swap partition is not getting used anyway.  If, per chance, you do actually run out of RAM while doing stuff, without the swap space the machine will crash.

There is a .deb called swapd which can make swap *files* instead of a partition.  I have it installed to, just in case I finally do something with my laptop which is so totally beyond its capacities.  Swapd is not developed anymore, as far as I know, but it is still used.  It is slower than a dedicated partition, but it does work.  There maybe limitations on how big or how many swap files it can make; I really am unsure on this.

---

