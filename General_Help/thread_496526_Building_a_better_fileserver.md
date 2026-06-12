---
title: "Building a better fileserver"
date: 2007-07-09
forum: General Help
---

### Post by glave on 2007-07-09
A little background first:

A little over a year ago, I began rebuilding my fileserver from scratch. My old server was sporting a 300g hd and getting full, when I realized that should something happen, I had an awful lot of media to lose. When building the new server, I decided to go with raid5 to help prevent disaster.

I built it with a promise card that sported 4 sata connections, and used 4 300g sata drives to make my array. I had a 2nd promise card for future expansion, and then I discovered that you cannot expand a raid5 array once it has been created without data loss. So I turned to LVM. Getting LVM setup on top of the array was a snap. Fast forward 1 year later and I'm running out of room.

I connect up 4 500g drives to the spare promise card, they come up like a charm. I expanded the LVM and now I had 2.2T at my disposal. Sadly, this is where it gets grim.

Yesterday one of the new drives died on me. The system hadn't marked it as failed yet, but my whole system had come to a crawl. I couldn't even shutdown, so after a while I killed it. I opened her up to unplug the suspect drive. Here's where it gets bad, because I grabbed the WRONG DRIVE. I boot up and now I'm down to 3 disks in the array, and 1 is trying to fail on me. I shut back down immediately and hooked up the good drive, came back up. The array started rebuilding the good drive because it had been offline, and then the failing drive decided it was time to truely fail.  Now I'm looking in syslog about all kinds of raid5 unrecoverable errors. I spent the majority of yesterday trying to figure out how I could reduce the LVM back to the original size covering the first array so that I could -maybe- recover at least that much data (which is actually 90% of it since the new array was mostly empty).  No luck there, I think either its not possible, or its beyond my skill level.

Question in point: What would be the best strategy I can deploy for trying to maintain a large amount of storage, reducing some risk of disaster, and leaving room for future expansion? I thought creating new raid array via promise raid expansion cards across LVM would be ideal, but now I'm not so sure.

---

### Post by Gizim on 2007-07-09
> **glave said:**
> A little background first:

A little over a year ago, I began rebuilding my fileserver from scratch. My old server was sporting a 300g hd and getting full, when I realized that should something happen, I had an awful lot of media to lose. When building the new server, I decided to go with raid5 to help prevent disaster.

I built it with a promise card that sported 4 sata connections, and used 4 300g sata drives to make my array. I had a 2nd promise card for future expansion, and then I discovered that you cannot expand a raid5 array once it has been created without data loss. So I turned to LVM. Getting LVM setup on top of the array was a snap. Fast forward 1 year later and I'm running out of room.

I connect up 4 500g drives to the spare promise card, they come up like a charm. I expanded the LVM and now I had 2.2T at my disposal. Sadly, this is where it gets grim.

Yesterday one of the new drives died on me. The system hadn't marked it as failed yet, but my whole system had come to a crawl. I couldn't even shutdown, so after a while I killed it. I opened her up to unplug the suspect drive. Here's where it gets bad, because I grabbed the WRONG DRIVE. I boot up and now I'm down to 3 disks in the array, and 1 is trying to fail on me. I shut back down immediately and hooked up the good drive, came back up. The array started rebuilding the good drive because it had been offline, and then the failing drive decided it was time to truely fail.  Now I'm looking in syslog about all kinds of raid5 unrecoverable errors. I spent the majority of yesterday trying to figure out how I could reduce the LVM back to the original size covering the first array so that I could -maybe- recover at least that much data (which is actually 90% of it since the new array was mostly empty).  No luck there, I think either its not possible, or its beyond my skill level.

Question in point: What would be the best strategy I can deploy for trying to maintain a large amount of storage, reducing some risk of disaster, and leaving room for future expansion? I thought creating new raid array via promise raid expansion cards across LVM would be ideal, but now I'm not so sure.

L2Backup lol
Sucks to be you :popcorn:

---

### Post by glave on 2007-07-09
> **Gizim said:**
> L2Backup lol
Sucks to be you :popcorn:

Something a little more constructive would be appreciated.

---

### Post by tribaal on 2007-07-09
> L2Backup lol
Sucks to be you 

Something less aggressive would be appropriate, as this is a help forum. If you need to make fun of someone, please go somewhere else.

- trib'

---

### Post by Gizim on 2007-07-09
> **glave said:**
> Something a little more constructive would be appreciated.

You really didn't look at the name did you? lol
btw charge your phone

PS. Maybe putting a sticker on the drive with the letter would help ..

---

### Post by glave on 2007-07-09
No one has any opinions on a fileserver?

---

### Post by Turboaaa2001 on 2007-07-09
I'm still a novice in the Linux world but quickly learning.

I first want to mention that the community here is usually much better than this.

With that out of the way I will say that from all my expertise in computer hardware and with the little knowledge I have of LVM you had the right idea. I think the weak link here is the fact that a failing drive is not properly being discoverd by the OS.

Here is what I would do in the future.

1. Continue what you were doing (unless someone more expirenced in LVM says otherwise)

2. When you suspect a drive to be failing run HD testing software. I use a free program that is bootable off a cd and does a really good scan of your system. I suggest using something like that to properly identify the right drive.

3. Unless the system is running as poorly as you stated, let the system eventually work itself out so there is less interuption.

Of course because of your performance hit you needed to do something soon, so you had the right idea but you shoud have run a S.M.A.R.T. test or something on the drive you thought it was before hand. 

What happend was you lost too much parity. The data on a RAID 5 set is split across all drives and has some of the data from all the drives spread out into parity on said drives. Generally of you loose more than 1 drive in a set then you loose data. So when you re-installed the good drive you lost 1 drive of parity. Then when the bad drive died you then had 2 drives of parity lost.  (I'm sure you already knew this, but I want to make sure)

I'm a PC technician and a die-hard builder but I can't help anymore than this. Like I said I'm new to Linux.

---

### Post by glave on 2007-07-10
I suppose continueing with LVM won't be so bad. This time I'm definitely investing in a few little stickers to physically place on my drives to I can identify easier.

---

