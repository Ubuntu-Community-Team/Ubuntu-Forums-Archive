---
title: "Upgraded ram to 2GB only shows 1.9GB?"
date: 2008-05-05
forum: General Help
---

### Post by thegreenblob on 2008-05-05
Hey, I just upgraded my ram from 512MB to 2GB (2x1GB), and in the System Monitor it says I have 1.9GB.

My question is... Is it normal for it to show a little less? Sorry if this is a newbish question, but just wondering, cause this is my first time upgrading ram on a system. :P

Thanks

---

### Post by TheExplorer on 2008-05-05
Yes, that's OK as Linux may occupy some for its system purposes.

---

### Post by thegreenblob on 2008-05-05
Ah. Thanks. All I needed to know. :)

---

### Post by .nedberg on 2008-05-05
Gibibyte / Gigabyte

[http://en.wikipedia.org/wiki/Gibibytes](http://en.wikipedia.org/wiki/Gibibytes)

That computer uses gibibytes (1024) while the manufacturer uses giga(=1000)

2*1000*1000/1024/1024=1,907

You are seeing all there are!

---

### Post by SEMW on 2008-05-05
> **.nedberg said:**
> Gibibyte / Gigabyte

That computer uses gibibytes (1024) while the manufacturer uses giga(=1000)

For hard disk sizes, yes; but not RAM!

With hard drives, the amount of space on a drive is fairly arbitrary; it's a function of the number of platters, the size of each platter, and information density -- it can basically be whatever you like, and manufacturers do indeed usually use SI prefixed rather than binary because it sounds like more.

But RAM doesn't work like that.  For technical reasons (relating to how it's addressed), it is ONLY available in capacities which are powers of two.  So a 2GB RAM stick will have exactly 2^30 bytes.  Not 2*10^9, not 2^10*10^6; 2^30.

Which means that, regarding the original question: I have no idea.  I have 2GB of RAM, and System monitor reports just that: 2GB.  Re TheExplorer's explanation -- "Linux may occupy some for its system purposes." -- Linux certainly is using RAM, but the "Hardware" section in System Monitor is there to show what hardware you have installed, not how much of it is not in use! (You can see free memory as a percentage of total elsewhere in SysMon, on the "resources" tab).

My guess is that it's a bug in System Monitor.  Maybe resulting from the use of floating point: 2GB is being interpreted as 1.9999999999999999312 GB or something, and then truncated to two significant figures?

---

