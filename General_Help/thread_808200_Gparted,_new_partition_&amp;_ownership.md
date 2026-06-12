---
title: "Gparted, new partition &amp; ownership"
date: 2008-05-26
forum: General Help
---

### Post by alcornmj on 2008-05-26
I must admit that I've been pleasantly surprised at how much Linux has grown since my first experience with it many years ago!

I'm now in the process of weening myself off WinXP as much as possible, and one of the things I've done is to dedicate half of my external USB drive, a Western Digital Passport, to EXT3.

Wow.  I had no idea this simple act would become so frustrating.  After a few hours forum mining, I found that, as many of you are probably aware, Gparted defaults the ownership of a new partition to /root.  One must then go to the command line to take it back.  Why?

It seems to me that something as basic as partition creation ought not be so confusing.  If Gparted is capable of assigning ownership, why isn't that an option on creation?

I suspect it has something to do with the parted library, since the same issues seems to happen with Qtparted and Gparted.  If so, can the developers of parted be contacted to add an option for ownership assignment during partition definition?

While I'm wishing, it'd be nice to be able to name the partition at that point too...

---

### Post by prince_niceguy on 2008-05-27
You can raise a bug in launchpad and hopefully it gets to the developers for enhancment.

---

