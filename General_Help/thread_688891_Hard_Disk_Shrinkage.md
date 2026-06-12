---
title: "Hard Disk Shrinkage"
date: 2008-02-05
forum: General Help
---

### Post by SMA11784 on 2008-02-05
How come your hard drive never has as much space as it says on the box?

My new computer has a 320 GB hard drive, but now that it's installed and everything, Ubuntu is telling me that its total capacity is 287.7 GB.  Now, I've noticed this before on other computers and thought nothing of it, but this is 32 GB.  My last computer didn't even have 32 GB (which I guess is pretty funny because it means the new box forgot more than the old box ever knew).

It's not as if it really constitutes a problem.  I still have plenty of space, but I'm still curious about what happens to a hard disk to cause 10% of its advertised space to just vanish.


(Western Digital Caviar SE WD3200AAJS from Newegg)

---

### Post by Shazaam on 2008-02-05
If you have gparted installed open it and it will show you the partitioned and un-partitioned space. Also, MFGR's like to use an incorrect value for their drives. A quick search will get you the answer.
My WD320SATA reads as 298gig:)

---

### Post by Rocket2DMn on 2008-02-05
There is a fair amount of loss because manufacturers measure HD space i decimal values, with a GB at 1,000,000,000 bytes when in reality a GB is 2^30=1,073,741,824 bytes.  Also, the ext3 filesystem that linux uses has a fairy large overhead.
That's where your space went :)

---

### Post by logos34 on 2008-02-05
it comes down to binary (base 2) vs. decimal (base 10) ways of measuring disk capacity (all OS's use the former, but drive manufacturers use the latter because it makes the hard disk look bigger)

And then when you format it ext3, you lose another ~5% by default ('reserved-blocks-percentage')

[http://www.hardwaresecrets.com/printpage/482/1](http://www.hardwaresecrets.com/printpage/482/1)
[http://www.pcguide.com/ref/hdd/geom/formatBinary-c.html](http://www.pcguide.com/ref/hdd/geom/formatBinary-c.html)

---

### Post by ryanVickers on 2008-02-05
they say 320Gb, it its really 3.2 billion bytes, which is less than 32gB, more like, well, ~287Gb ;) (using 1024 instead of 1000)

---

### Post by SMA11784 on 2008-02-06
You mean 320 billion bytes.  3.2 billion would either be 3.2 GB or 2.98 GiB

320,000,000,000 / 1,073,741,824 = 298

So I'm only missing 11 gigs.  I knew the "1 TB" drives weren't really 1024 GB.  It never occured to me that they all did that.

---

### Post by ryanVickers on 2008-02-06
yea, lol sorry, but you get the point :p

---

