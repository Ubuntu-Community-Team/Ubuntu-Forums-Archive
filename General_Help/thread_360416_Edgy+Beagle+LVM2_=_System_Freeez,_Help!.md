---
title: "Edgy+Beagle+LVM2 = System Freeez, Help!"
date: 2007-02-13
forum: General Help
---

### Post by fotakis on 2007-02-13
Hello all,

I have been looking around to see if anyone has encoutered this problem recently. First of all here are my specs:

Ubuntu Edgy
Uname -r =  2.6.17-11-generic
Beagle = From the repo
LVM2 = /home
Intel Core DUO 

At first I though the problem arised when I upgraded my kernel from 2.6.17-10 to 2.6.17-11 a couple of days ago, my computer just freezes. I mean nothing works, nothing moves, keyboard and mouse dead, only option is to hard boot.

So I started backrolling some of the changes I made in that period, one of them was migrating my /home partition to a very large 700GB logical volume which spans 2 partitions and 1 hard disk. The other change like I said was upgrading the kernel (which in turn meant I had to recompile the nvidia driver) and finally I read an article in LFX which talked about beagle, deskbar and tomboy, and I gave it a try.

After a couple of days of system freezes which would occur every 40 minutes, I figured out that the problem lied with the above combination and beagle+mono. 

Because none of the logs show anything going wrong, I now turn to the forum to see if anyone is encountering the same problem and how I would go about and solving it, I really want beagle+tomboy+deskbar :-)

Best Regards,
Fotis

---

### Post by fotakis on 2007-02-14
anyone?

---

### Post by fotakis on 2007-02-16
So I am guessing I am either asking in the wrong section, or I will just have to live without beagle.

---

### Post by fotakis on 2007-02-26
Hello all,

I am desperately tyring to get to the root of the problem of this, so if anyone can point me in the right direction? 

I have a fedora install at home with LVM and I don't encounter the problem, so I am guessin it is only on my work pc.

I have reviewed all the beagle logs and there is not a single mention of error or exception, so I don't know where to start from?

Best Regards,
Fotis

---

