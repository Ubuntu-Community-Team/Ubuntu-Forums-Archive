---
title: "Need help with partitions on an existing installation (2 partitions + swap)"
date: 2014-01-10
forum: General Help
---

### Post by hot.sauce.jake on 2014-01-10
It's been 7 years since my last Ubuntu install *gasp*...

Well I'm back into the folds...

I had to do a WEEK of workarounds to finally get my installation working on my Macbook Pro (early 2008 model - macbookpro 4,1).  I found a few tutorials to make it work.

My method was to install Ubuntu 10.10 and slowly upgrade to 13.10.  I had to do this because my wireless would only work with 10.10.  Upgrading left it intact I guess.

My problem:

I followed the advice of someone to create 2 partitions.  One at 16GB with the / mount point (linux system files I guess).  The other was around 250GB with the /home mount point (for all my files).

The problem is - I installed a lot of software and it's mostly already filled the 16GB.  Is there a way to extend the 16GB partition so I don't lose my progress.... or do I need to start over and just create one mount point.

I hope I followed your jargon well enough to detail my problem.
[B]
TL;DR - I'm running out of disk space in one partition.  Can I extend it and take away from another partition?[/B]

---

### Post by jfolsom2 on 2014-01-10
If you can boot from a livecd, you should be able to use gparted or qtparted to graphically resize those partitions.

---

### Post by nilla78ro on 2014-01-10
maybe you can try to cleanup a bit , try : [FONT=Ubuntu Mono]sudo apt-get autoremove[/FONT]

---

