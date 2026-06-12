---
title: "Partitioning Recommendations for ubuntu user"
date: 2004-11-19
forum: General Help
---

### Post by BoyOfDestiny on 2004-11-19
Hi, I have 2 150gig sata drives (raid 0) and a 250 pata gig drive. 
The system is an opteron on nforce3 SK8N, and as I do hope to eventually wipe windows off (ubuntu is great!), 
I was contemplating for the main raid, an 

8 gig root (for ubuntu 64 and perhaps chrooting 32-bit),
 2 gig of swap (1gb ram currently), 
and the rest /home. Everything would be reiserfs except the swap...

Is this a good plan? I use the machine for general "office desktop etc", retro gaming, listening to music, watching video, cd-burning etc. 

I hope this is a "relevant to ubuntu post", 
just to make sure, has anyone had luck putting it on the software raid of promise that is included on the nforce3?

---

### Post by TravisNewman on 2004-11-19
I'd suggest more than 8 gigs for the root partition. You might want to get into some games with that badass system and that would start taking up some hard drive space pretty quickly. I'm using more than 8 gigs on my Ubuntu install already. I mean, you've got a lot of space, my advice would be to go for about 20 gigs for the root. That still leaves you with almost 130 for the /home.

---

### Post by HungSquirrel on 2004-11-19
Well, that depends on whether he wants to install his games to /usr/local or to ~, but I definitely agree that with that much hard disk space you might want to give / an extra few gigs just for extra room, in case you do want to install something large in /usr.

OpenBSD's install manual sums it up best:
[quote="OpenBSD"]We would rather have a few hundred megabytes of unused space than a kilobyte too little.[/quote]

---

### Post by dataw0lf on 2004-11-19
Here's my setup (on two 150 gig drives and a 100 gig drive);
/ - 20 gigs
/usr - 20 gigs
/usr/local - 60 gigs
/tmp - 3 gigs
swap - 1.5 gigs (1 gig ram)
rest in /home
I have a habit of partitioning the /tmp pretty high, but it's always a good idea to partition it in any case.

dataw0lf

---

### Post by TravisNewman on 2004-11-19
I should partition more than I do, I only have two 60 giggers, / and /home, and the swap of course. I need to change that up quite a bit.

---

### Post by mrt on 2004-11-19
With a gig of ram, is swap really necessary?  I have 512 ram in my ubuntu box, and it runs just fine without swap space.

---

### Post by FLeiXiuS on 2004-11-19
[QUOTE=mrt]With a gig of ram, is swap really necessary?  I have 512 ram in my ubuntu box, and it runs just fine without swap space.[/QUOTE]

I always partition

/boot
/root
/
/usr
/home

It solves a lot of problems when something fails and crashes the install.  Usually an ID-10-T

---

