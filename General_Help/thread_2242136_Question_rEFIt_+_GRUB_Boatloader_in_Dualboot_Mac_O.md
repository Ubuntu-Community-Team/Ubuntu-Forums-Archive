---
title: "Question: rEFIt + GRUB Boatloader in Dualboot Mac OS X &amp; Ubuntu 14.04"
date: 2014-08-30
forum: General Help
---

### Post by caruso2 on 2014-08-30
Hi there,

I am completely new to the whole Ubuntuworld and wanted to give it a shot by installing Ubuntu on my Macbook Pro.
Through the help of guides of this forum, I was able to install Ubuntu parallely to Mac OS X.

Now it is like this: When I boot my Macbook I can see the boot menu of rEFIt where I can choose of Mac and Linux.
If I choose Mac, everything works fine. My Questions are regarding the second option: When choosing Linux I am getting to the GRUB Boot loader, where I have the options of 
1) Ubuntu
2) Memory Test
3) Memory Test Alternative
4) Mac OS X (yes, again)
5) Mac OS X (safe mode)
and I think 6) Ubuntu in safe mode

Is there a way to modify GRUB in a way, that, after choosing Linux in the rEFIt menu, it automatically starts Ubuntu?

Is there a way in rEFIt to set a automatic boot OS (e.g. Ubuntu) so that I only have to step in if I want Mac to be booted?
I've read somewhere that rEFIt is probably overwritten (i.e. dualboot no longer works) when Mac OS X is updated. Is that true or will that setup endure short termed future?

Hopefully you can help me here with these detailed questions.

I thank you in advance,
have a good time,

Caruso

---

### Post by yancek on 2014-08-30
> Is there a way to modify GRUB in a way, that, after choosing Linux in the rEFIt menu, it automatically starts Ubuntu?


No.  You are first seeing the rEFIt menu so you would have to modify the rEFIt menu to do that which may or may not be possible.  I imagine it  isn't directly booting Ubuntu but just chainloading which is why you see two menus.  I've never used rEFIt so can't help with that.

---

