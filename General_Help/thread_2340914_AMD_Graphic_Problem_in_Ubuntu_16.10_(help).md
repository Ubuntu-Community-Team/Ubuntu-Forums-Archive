---
title: "AMD Graphic Problem in Ubuntu 16.10 (help)"
date: 2016-10-23
forum: General Help
---

### Post by vahed on 2016-10-23
hi guys! :(

Please Help me

I have an Acer Laptop with AMD Radeon R7 M265 Graphic Card..

But since I install Ubuntu 16.10 on my laptop That OS don't Support My Graphic Card 

and I have many Graphic crash and Graphic Problem in Ubuntu..

What should I do?

This Pic is about system setting === > Software & Update ====> Additional Drivers

[IMG]http://www.axgig.com/images/30197012007754692819.png[/IMG]

---

### Post by T.J. on 2016-10-24
All that means is that it is not supported in the AMD official driver in 16.10 at this time.  By default, you are probably already using the open driver.  If I might suggest, 16.10 is not for regular users.  It's intended for developers and enthusiasts, and it has more bugs than an LTS release.

You might want to consider using 16.04 LTS unless you have a reason to upgrade.

---

### Post by mörgæs on 2016-10-24
> **vahed said:**
> 
But since I install Ubuntu 16.10 on my laptop That OS don't Support My Graphic Card 


It certainly does support the card, else you wouldn't have a picture on the screen.

Which other versions have you tried?

---

### Post by vahed on 2016-10-24
Hi
TNX 4 ur answer :)
I am a programmer and software repositories are old in 16.04.1 version.
but how to downgrade ubuntu 16.10 to 16.04.1?

---

### Post by vahed on 2016-10-24
> **mörgæs said:**
> It certainly does support the card, else you wouldn't have a picture on the screen.

Which other versions have you tried?

i tried 16.04.1 LTS

---

### Post by mörgæs on 2016-10-24
In that case I think you should try a fresh install of one of the other 16.10 Buntus, that is X/Lubuntu or Mate.

---

### Post by T.J. on 2016-10-24
> **vahed said:**
> i tried 16.04.1 LTS

I believe we have a misunderstanding here. I think it is very likely that  your R7 is one of the ones that is not supported by AMD in the new  AMDGPU driver. So it is not available on the driver manager to install.  AMD created a huge mess in support, and it is AMD's fault - not Linux's. AMD has treated us all with spotty support - which is one of the reasons I switched to Nvidia after 5-7 years.

Just because there is not an official AMD driver listed in the driver manager does not mean that your display is not working or unsupported. Since you have a working display at all (instead of a black screen) - then that means  you are already using the default Xorg driver.  The default Xorg driver is perfectly adequate for use.  I use it myself, because  AMD's official drivers are full of bugs or have support gaps.


There are three AMD drivers.  The default community (Xorg) driver, which you are using right now, the older FGLRX driver, and the AMDGPU driver.  FGLRX was the official driver, but AMD pulled support for it.  The new one that they do support - the AMDGPU driver does not support many cards, including some R7 cards - and AMD did that on purpose.  That leaves the Xorg driver as the only one guaranteed to work.  It is installed by default. 


You have three options that I can think of at this point:

1. You can just keep using the Xorg driver provided by Linux/Xorg - which works very well.
 2. You can follow AMD's recommendation and stick with Ubuntu 14.04; or you can switch to Debian 8.  Both of which have support for the commercial driver provided by AMD.
3. You can install Windows and use Virtualbox or Hyper-V to run Linux programs.  Of course, I cannot guarantee that AMD will give you any better driver support on Windows, either.

Unless you need the support for CAD or Steam gaming (a few games need the commercial driver), I suggest #1. As I mentioned, I use it myself, and you don't need to do a thing.

---

### Post by QIII on 2016-10-24
T.J.:

Please take care - you are indicating a good deal of misunderstanding with regard to the AMD drivers yourself -- especially the length to which AMD is going (at great expense for which they will reap little return) to improve things.  AMD is in the process of ***vastly improving Linux support***, not walking away from it.

Both Radeon and AMDGPU are open source drivers.  AMDGPU supports a limited number of cards right now, but it is being extended backward to earlier cards.  That can only go back so far due to the physical design of older cards.  The Radeon driver is being rapidly improved.  AMD is working very closely with open source developers (most of them from Canonical) to provide that support.  

AMDGPU-Pro is the proprietary add-on to AMDGPU.  Let me put that another way:  AMD's proprietary driver is built on an open source driver.

There is a good deal of road construction going on right now and the ride is bumpy.  But AMD is doing exactly what we have been asking them to do for years:  provide genuinely full-service open source support.

So let's not spread inaccuracy and FUD.

Now, to be honest, there is no harm in recommending the purchase of an NVIDIA card right now if a user cannot afford an AMD GCN 1.2 or better card just at this moment.  But I can tell you quite for certain that a GCN 1.2 card with the AMDGPU driver works better than with fglrx -- and better yet with AMDGPU-Pro.  AMDGPU is being developed to work with cards back to GCN 1.0 (but that is the physical limit to which they can go back) which will include most HD 7000 series cards.  Buyers simply need to be sure what they are buying and what is supported by AMDGPU at the time.

Now.  By  way of explanation for everyone.  

When 16.04 and later are installed on machines with AMD graphics, the installer looks at the GPU.  If it is supported by AMDGPU, AMDGPU is used.  If not, Radeon is used.  To determine which is being used, you can simply list the loaded modules and grep for radeon or amdgpu.

```
lsmod | grep radeon
```
```
lsmod | grep amdgpu
```

One will return results, the other won't.

No additional GPU driver will be listed because one of the two choices, Radeon or AMDGPU, will have been chosen by the installer and used.  To get AMDGPU-Pro, which is the open source AMDGPU with the proprietary overlay, you need to have a GPU supported by AMDGPU (lsmod that) and then go to the AMD website.

All of that said:  vahed, we need to know the results of the commands above to know which module is loaded before we can be of much further help.

Thanks.

---

### Post by T.J. on 2016-10-24
> Please take care - you are indicating a good deal of misunderstanding with regard to the AMD drivers yourself 

Good to see you again!

Fair enough.  I had no intention of making things worse.  You are right.  There are two versions of the AMDGPU driver.  I lumped the open AMDGPU with Radeon as "the Xorg driver" out of habit.  If I may say so,  you are mistaken about me at least.   I understand the situation well, but it doesn't help people who are caught in the middle of this mess, sadly.


> AMD is in the process of ***vastly improving Linux support***, not walking away from it.


Oh I agree.  

It is the way that they approached the upgrade that leaves much to be desired. It's a matter of keeping the support your customers need at the present time in place for the expected lifetime of the card.  They already do so on Windows.  There is nothing wrong with expecting the same courtesy for Linux in the same time period. We paid the same price that Windows users did, and it is not an unreasonable expectation considering that AMD works to deliberately attract Linux users to buy its hardware.    The R7 265 is only 2 years old. Considering that, along with the FGLRX driver was still prone to corruption after years of complaints, and more recently the 480 RX debacle, I would say my assessment of "spotty" support was fair.  AMD is only proactive in fixing problems afterward, not avoiding them when they should be obvious.

This is my opinion.  You are welcome to disagree.
  

It is also true that AMD is not entirely to blame in the sense that communities can be hard to work with.  Canonical knew that this was a going to be a problem, and could have stayed with Xorg 1.7 for 16.04 LTS release, and avoided this driver issue altogether. There is definitely room for improvement in the Canonical/AMD relationship.

> "But I can tell you quite for certain that a GCN 1.2 card with the AMDGPU driver works better than with fglrx -- and better yet with AMDGPU-Pro."

Of that, I have no doubt my friend.
 
But it is really digressing from the point of this post.  I could be wrong, but it is likely that there is very little that we can do other than suggest a rollback to an older version, or to remain using the Xorg driver (Radeon or AMDGPU).  I do not think that AMDGPU-Pro supports the 265M mentioned here, and FGLRX is unusable on any Ubuntu 16.x. It seems likely that the lack of options in the driver manager means the OP is likely one of the "unlucky" ones left out at present - which is why I said what I did.


Take care! =)

---

### Post by mastablasta on 2016-10-25
> **T.J. said:**
> 

It is the way that they approached the upgrade that leaves much to be desired.  The direct result of the current situation is that they inconvenienced a lot of people who need  OpenGL 4.x. They could have provided maintenance (but no updates or bugfixes) for FGLRX until the older R7s are at least 5 years old.  The R7 265 - for example -  is only 2 years old.  It's a matter of keeping the support your customers need at the present time in place for the expected lifetime of the card.  They already do so on Windows.  There is nothing wrong with expecting the same courtesy for Linux in the same time period. We paid the same price that Windows users did, and it is not an unreasonable expectation considering that AMD works to deliberately attract Linux users to buy its hardware.  


14.04 is supported until 2019. it has fglrx avaialble.. 
 
> 

I would say my assessment of "spotty" support was fair. This is my opinion.  You are welcome to disagree.
  

i agree with this assesment.

> 


It is also true that AMD is not entirely to blame in the sense that communities can be hard to work with.  Canonical knew that this was a going to be a problem, and could have stayed with Xorg 1.7 for 16.04 LTS release, and avoided this driver issue altogether.  As a programmer, if I had to chose an option knowing the problems others would have, I would have chosen that. It makes the most sense.   It would have also given AMD more time to solve its release issues, and no one would have known the difference.  You could argue hindsight - but it really wasn't IMO - the whole thing could have been avoided but deliberately wasn't.  That's a bad support policy when Ubuntu is considered a premier Linux distro.  

There is definitely room for improvement in the Canonical/AMD relationship.


there was talk of possible new version of fglrx for 16.04 as well. i am not sure if this was shelved or what, but i agree they (AMD) could have provided support (no major update, just suppot) for the latest LTS.
a laptop i bought in 2012 no longer has propper GPU driver support in 2016. so i stayed on 14.04 for now.

---

