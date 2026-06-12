---
title: "32 bit on AMD64: what kernel?"
date: 2007-03-05
forum: General Help
---

### Post by jjf on 2007-03-05
I have an AMD64 right now running the i386 kernel.  I don't want to "upgrade" to the AMD64 kernel, but I'd like a performance boost if I can get one.  Will some other 32-bit kernel give a performance gain?  K7 or i686?

Thanks.

---

### Post by lavinog on 2007-03-05
you could shrink your partition (make about 6gigs of space) using gparted (you may have to do it from the live cd)
and just install edgy 64 on that partition and give it a try.
this way you can continue using your current setup until you have the 64bit problems worked out
but to answer your question i believe the i386 kernel already has support for k7 and 686. (type 'uname -a' and you should see i686). therefore 64 would give you the best performance increase.
yes it is kind of a doozy to setup, but there is enough help on this site to get everything running...just takes time.
I think feisty should be out soon...you may want to wait and install that for the best performance.

depending on what you do, you may not notice a performance gain, or it might be so small that you can't tell, but with it you know you are getting the best your processor can offer. 64bit support is picking up really fast why not jump on the band wagon.

---

### Post by fragos on 2007-03-06
Unless you want to run more than 4GB of memory I doubt you will be able to notice a difference.  The best way to improve performance on an existing system is to add enough memory so that you no longer use swap space on the disk.  The command free will tell you how much swap you're using.  Going from 256MB to 512MB made a noticable difference on my AMD Sempron 2800+.  I still used some swap so I ultimately added a second 512MB.  At 1GB I use no swap space on disk and by using two identicle memory parts I got a 10% increase in memory access speed because of how DDR memory takes advantage of multile devices.  I run the i386 kernel as some software like Flash only comes in 32 bit versions.

---

