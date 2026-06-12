---
title: "Best file system to use?"
date: 2006-10-19
forum: General Help
---

### Post by WalmartSniperLX on 2006-10-19
Just wondering what are the possible file systems available for running linux on, and which one is best. When I installed I used the default ext3 :D

---

### Post by BitTorrentBuddha on 2006-10-19
I've heard that reiserfs is a bit faster but bad if your system crashes. I would choose ext3, I assume it's default for a reason.

---

### Post by moore.bryan on 2006-10-19
*from what i've read, reiserfs can be buggy and have a whole boatload of problems, especially when it crashes.  although ext3 may be slower, there are tips & tweaks around the forum for making it a bit faster...*

---

### Post by Kateikyoushi on 2006-10-19
It is like asking which is the best car in the world.
It depends, each has its own strong sides and dark side.
If you aren't willing to dig deep ext3 is fine.

I partitioned my drive before, to use xfs on my movies partition because it is bigger wiith big files uses big cache i am on notebook so no problem with that, powerloss won't occur, it is said that it stresses the cpu more I did not notice or my Pentium M at 600Mhz might be strong enough. ;)
I had jfs for system, later changed it to reiser and now ext.

Search a bit about the topic but do not expect miracles, even with the right filesystem for the partition's purpose hard to feel the difference.

[This is what I read right today.]("http://www.oracle.com/technology/pub/articles/calish_filesys.html")

---

### Post by kerry_s on 2006-10-19
I've been using JFS and let me tell you this sucker has been solid, we've had several power outages here in hawaii and it would go out while i'm on the web, or here in the forums. It has always booted right back up, no checking the disk because of unclean unmount, then rebooting again, none of that it just boots up normal, the powers gone out about 5 times so far and i'm not having any problems. It surprized the hell outa me, i thought for sure my system was toast, Even my dads XP has not held up, it's blue screening like crazy.LOL. I think from now on i'll only be using JFS. :-D

---

### Post by Old Pink on 2006-10-19
ext3, or the new upcoming ext4. **[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)**

---

### Post by lapsey on 2006-10-19
ZFS

(when it is ported..)

---

### Post by WalmartSniperLX on 2006-10-20
Thanks everyone :D So I guess it's all weighed on a balance. :cool:  But, so far for me, ext3 is working fine so I guess I wont have to worry about it afterall :D

---

