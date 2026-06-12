---
title: "Resize partitions"
date: 2007-11-04
forum: General Help
---

### Post by cartisdm on 2007-11-04
Here's the deal.  I know I've seen a few threads posted around talking about resizing partitions but I was hoping to get a little more of an idiot proof walk through.  I did a fresh install of Windows XP and Ubuntu 7.10 last night but I put windows on the large partition and Ubuntu on the smaller one.  I'm sure I could figure this out but I was a little thrown off by the NTFS differences and I don't want to make anything not work with Ubuntu's filing system because I'm new to linux.

[IMG]http://photos-869.ll.facebook.com/photos-ll-sf2p/v150/195/50/7822869/n7822869_35064730_6445.jpg[/IMG] 

Any help would be great!!

---

### Post by minus198 on 2007-11-04
So what you want is linux on a big partition and windows on a small one?

If so and you installed linux and windows yesterday, I say that you should reinstall.. Cause resizing partitions is never good.

---

### Post by cartisdm on 2007-11-04
Yea linux on the large partition and XP on the smaller one.  I would just do it again but I've already put a lot into both O/Ss.  I ran all my updates, upgraded Ubuntu to 7.10 from 7.04, customized all my settings and installed a lot of plug-ins that I just don't feel like doing again so I'm trying to save myself the trouble

---

### Post by njparton on 2007-11-04
Sounds like a job for Partition Magic to me!

Also check out the gparted live CD. It's a 50MB download and it should let you resize your ubuntu partitons. You won't be able to do that when you're logged into ubuntu.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by bingoUV on 2007-11-04
Before spending currency on burning a new CD (for gparted), try booting from the live CD of ubuntu from which you installed. In this you can run gparted. 

In the GParted menu, select show features. See whether NTFS resize feature is available (it has been at least since feisty). Also, see if ext3 move as well as resize is available (it is available in gutsy live cd).

---

