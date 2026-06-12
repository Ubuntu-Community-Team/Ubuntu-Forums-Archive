---
title: "Drivers for AMD and Ubuntu 16.04"
date: 2016-05-17
forum: General Help
---

### Post by reduxpl on 2016-05-17
Hello!
A few days ago I upgraded xUbuntu from 15.10 to 16.04. Since I wasn't really tracking what has changed in the latest release, after upgrading I've just reenabled all the PPA's and run apt-get upgrade - right now I'm running the mesa driver from padoka's PPA. But I've just recently found out that there are some major changes in terms of AMD drivers. From what I understand, fglrx is now abandoned and AMD will fully focus on their open-source driver, AMDGPU. So, I have a few questions:
[LIST]
[*]Apparently, the AMDGPU driver is going to work only on GCN cards. Does that include Radeon R9 280X?
[*]Seems like you can also run the AMDGPU-PRO driver, "which works on top of the open-source AMDGPU kernel driver". What does it mean for an "average" user who's looking for gaming on Linux/Ubuntu?
[*][Benchmarks on Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=3") are showing that the performance of AMDGPU driver is better than mesa but still worse than fglrx. Results are shown on 5 GPUs, none of which is the same as mine. I'd like to try how this driver works anyway. How do I install it? Should I uninstall Liquorix kernel first?
[*]What else do I need to know about AMDGPU and AMDGPU-PRO?
[/LIST]
Thanks for help in advance!

---

### Post by QIII on 2016-05-17
Hello!

For now, only GCN 1.2 cards are supported.  Possibly made to work on GCN 1.1 cards (currently experimental support is available if you want to roll your own kernel) or even GCN 1.0, but the last two are not certain.  The list of what works includes the R9 380X cards but not the 280X.  285X maybe.  I'm running an R9 380X.  Any Tonga or Fiji chipset card will work.  My R9 290X defaulted to Radeon, so I'm selling it.

For the moment, the AMDGPU Pro driver is available for testing for 14.04 only, so I'm not taking the chance on problems.  I'll wait a bit. It's difficult to say what that means for gamers.  We don't know, for instance, whether games will even run on the AMDGPU drivers if they have been designed for fglrx.

The benchmarks on Phoronix have been improving as the work on AMDGPU progresses.  My results with the Phoronix Test Suite currently indicate that I am getting *better* performance, even without the proprietary "Pro" parts of the driver.  As for your kernel, I don't know.  I can say that the AMD engineers have be working closely with the Canonical developers -- almost exclusively -- so you are more likely to find support in an Ubuntu-tailored kernel if you don't want to recompile.

What else do you need to know?  What else do you want to know?  Phoronix pretty much covers anything from soup to nuts, and there are a number of forums out there -- some of which the AMD engineers frequent.

This is going to be a difficult, wild and sometimes fun Summer!

Cheers!

---

### Post by reduxpl on 2016-05-17
Well, I wanted to know how much of an impact AMDGPU-PRO (or a lack of it) is going to have on performance and what other differences in daily usage will the "hybrid driver model" cause. But I'm going to read that entire article first because I admit I was only looking to benchmarks :)

Seems like it's going to be a fun summer indeed, hoping for Radeons to get a good performance boost!

---

### Post by QIII on 2016-05-17
For daily usage you'll see little difference even without the "Pro".

---

