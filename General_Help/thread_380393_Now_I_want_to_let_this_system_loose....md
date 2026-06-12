---
title: "Now I want to let this system loose..."
date: 2007-03-09
forum: General Help
---

### Post by hppyfngy on 2007-03-09
Hey, I now have a lovely Edgy/Beryl install with everything working exactly the way I want it to.  :) 

Now I want to f**k with it, but I don't want to ruin it.  (I'm not that great with the command line)

What files do I need to make sure I have backed up before I get silly with this thing?

Is there a recommended method of "system backup" or "restore" as there are in some other operating systems?

):P

---

### Post by srt4play on 2007-03-09
Before getting silly with it,  I use partimage to backup my system.  It's in universe.

---

### Post by hppyfngy on 2007-03-09
Thanks, I'll give it a try.

---

### Post by hppyfngy on 2007-03-09
Well, I'm having trouble with partimage.  I begin the backup but I'm then told I don't have enough room.  

I'm not really sure how to even check to see how much space is left on the disk, but there should be plenty!

---

### Post by Tomosaur on 2007-03-09
The general advice is:

If it ain't broke, don't fix it.

You have to at least expect that something will go wrong somewhere, it's part and parcel of learning. Best thing to do would be to back up your home directory - at least that way you'll keep your personal stuff and most config - it should lower the time spent getting your system back to normal after that imminent point where you do hose your install. The /etc directory is where most program data goes (configuration etc), and it's likely thats the area you'll be playing around in the most, so you should probably back that up.

---

### Post by Redeyes_Gambit on 2007-03-09
If you want a really easy backup/restore try the one in automatix. It's under the "utilities" section.

---

### Post by hppyfngy on 2007-03-10
> **Tomosaur said:**
> The general advice is:

If it ain't broke, don't fix it.

You have to at least expect that something will go wrong somewhere, it's part and parcel of learning. 

Believe me, I know this is true.  Over the past 5 years or so I've tried no less than 50 flavors of Linux, and I've learned a lot, but this is the closest I've been to making a Linux box my every day user.  Not that I don't like it, I just don't have time to really really learn the commands and the system intricacies.  

It ain't broke now, but it probably will be...:p

---

### Post by srt4play on 2007-03-11
Were you able to figure something out for backing up your system?

---

### Post by hppyfngy on 2007-03-14
> **srt4play said:**
> Were you able to figure something out for backing up your system?

Yes and no.  I think partimage is probably the best answer and I got it on a boot cd called SystemRescueCD:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

The problem is you need an available partition or drive to back up to, and I currently don't have another partition or drive for what would be about a 25gb backup (uncompressed.)  

I think I'll probably create a new partition and use partimage, I just haven't done it yet.  
:)

---

### Post by srt4play on 2007-03-15
That's a good plan.  I have an external drive I use with partimage and it works very well and is very quick too even with compressing the image with gzip.

---

