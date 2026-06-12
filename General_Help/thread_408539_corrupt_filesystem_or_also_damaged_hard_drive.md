---
title: "corrupt filesystem or also damaged hard drive?"
date: 2007-04-13
forum: General Help
---

### Post by jdk_ on 2007-04-13
Hi there,

I have a laptop which has been running up-to-date dapper since its release, it had been working fine except for some random, not very frequent freezes. 

Since a week or so ago it doesn´t boot anymore, it gets to the "Uncompressing Linux ..." message and the hard disk starts to make the worst noise I´ve ever head form such a device. I can only blame the times it has lost power abruptly (power management doesn´t work well), but oddly enough nothing like that has happened recently. I guess the problem is just with with my root partition, as I have windows installed on the side and it boots perfectly fine (which doesn´t help me at all as it is in prstine form, with no access to my files and I really don´t plan to use it).

So I wonder: should it be a hardware problem or just a corrupt filesystem?

In the hope of the first I´ve tried to boot some live cd´s I had at hand (kubuntu 6.06, an old knoppix and the latest system rescue cd) in order to get a couple of things out of my home partition and probably delete the root partition for a reinstall. The problem: all of them freeze at some point when they go for the damaged partition, giving some error messages related to certain places in the filesystem or to udev being unable to pupulate /dev, and I couldn´t find boot options to prevent this and later mount the other partition manually. Later I did delete the root partition from the partition table using cfdisk from slackware cds I have, still nothing but windows boots.

Any clues will be much appretiated!
(Of course, I searched the forums first but nothing I saw seemed to apply here)

---

### Post by rmemm on 2007-04-13
I don't like the noise thing.  To me noise sounds like bad drive.  I had a drive go bad.  Some times it would work sometimes bad noise.

One thing you might try is one of those command line emergency cds, they don't have all of the complicated overhead that can cause problems when a system is on the edge.  In fact I used one such CD to recover my bad drive a year or two ago.  Mine actually was something GNU was sending out but there are a bunch of others.

I don't know why your hanging -- could it have been a swap partician issue not a root partician issue?  Sometimes some of these cds do use swap files I think.

Other thing you can do -- is use dd to copy particians -- if you have problems with tar or something like that -- sometimes dd can cause less problems as there less head movement -- though the downside is you have to copy the whole raw partitian somewhere.

Rob

---

### Post by jdk_ on 2007-04-14
Hey memm, thanks a lot for your reply. 

So far I´ve used a Slackware cd to delete both the root and swap partitions I had ---and even created new ones without troubles---, and I can even mount my home partition when using that cd, so it shouldn´t be too difficult to get files out of there. Btw, it was dazzling to see that my root partition appeared as being of type Amoeba instead of Linux Reiser (as it actually was) in the partition table, that´s just crazy!

Anyway, my main worry is that I reallly need a working computer and, as things are right now, I won´t be able to install anything (feisty!) on it. I just want to exhaust my possibilities before going for a new hard drive.

---

### Post by rmemm on 2007-04-14
Glad to hear things look positive.

One thing I didn't say.  If your going to continue to use the drive -- you may want to back up everything you can -- if it's the drive -- it's usually all down hill and things can be unpredictable.

Otherthing you could try is to run the badblocks utility on any new partitians you create before you bother formatting them.  There is a destructive write mode which can test rw stability.  It erases the whole partician contents -- so don't use it on partitians with data -- and the partician you run it on will have to be formatted afterwards -- but Linux does have this tool.  Generally it's good to backup things before doing this too -- it will do alot of IO which may kill your drive if its on the edge -- and doing partician level work is always a way to loose data if you make a mistake or something unexpected happens.

Also if you don't have it -- you should save the partician table settings from fdisk or another such tool so you need exact sector locations of your particians -- this is incase you loose your partician table.  Make certain you have sectors as fdisk has a cylinder and a sector mode for data display.

Anyway, some ideas.

Rob

---

