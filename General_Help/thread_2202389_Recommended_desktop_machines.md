---
title: "Recommended desktop machines?"
date: 2014-01-28
forum: General Help
---

### Post by archaeometrist on 2014-01-28
I'm presently using an eight year old desktop running a d-945 processor and Intel motherboard.  They're starting to have thermal problems (along with the video card) and pop up warnings whenever the weather is warm or humid.  I've cleaned the heatsinks, the boards, changed the heatsink compound, added in a custom cooler to the processor, but it still has the problem.

The computing demands that I'm starting to encounter (I do a lot of heavy number crunching and video-intensive stuff like GIS, stitching together huge picture files, intensive sound processing, etc.) is starting to run slow.  I also have to run some programs in a virtual machine (wXP environment because the software will only run on Windows) and that is marginal... sometimes I have to wait on it and it's slow.

We're talking about buying a new desktop, rather than wait until this one goes down (I can't afford to have to be without a system for any length of time).  I've been looking at a Dell Optiplex 7010 minitower (with i7 3770 processor, 16Gb ram, 1Tb hard drive, and so on) but it looks like that may not be compatible with Ubuntu 12.04LTS.  I've also looked at an ASUS M51ACUS002S desktop (from Best Buy) which has features I like, but may not be reliable enough (some negative reviews).  I'd be paying about the same price for either one.

Will these work with Ubuntu 12.04LTS?  (I also will be running a Gnome desktop - I don't like that new one.)  How good are they?  If they aren't recommended, what would be a good Intel-based desktop in the $900-950 range (my budget for new equipment)?

I don't have time to go shopping for individual boards and so on and put a system together - I'm a graduate student and barely have the time to install Ubuntu and switch over.  I've already got dual monitors and will need to install extra sound cards - for what I do I usually run three cards including the built-in audio.  I would need to be able to run multiple windows including at least one virtual machine at the same time - at least four cores on the processor and 3.4Ghz speed plus fast ram and video.

Any suggestions?

---

### Post by oldrocker99 on 2014-01-29
You might want to try the MATE desktop; it's pretty lightweight, and is a fork of the old GNOME 2.3 desktop (which was the default Ubuntu desktop before Unity, the current one). It gives me the same comfortable feeling I had when I started lo these 6 years ago with Hardy Heron. Check out [http://www.mate-desktop.org](http://www.mate-desktop.org).

---

### Post by deadflowr on 2014-01-29
Is this thread about a desktop computer or desktop environment?

---

### Post by mastablasta on 2014-01-29
you can check here: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

but usually they have older models in that list.

you can have a look at system 76 they have nice i7 maschines in your price range. and from what i read they have quality builds.

what makes you think the dell won't be compatible? what are it's components?

---

### Post by robin7 on 2014-01-29
I'm running Xubuntu 12.04 on a 12-year-old Dell Dimention with a Celeron 2.5 Gig processor and 512 RAM.  It runs beautifully.  The Xfce desktop environment in Xubuntu is configured for elegance and simplicity, and the fact that it runs so nicely on this old computer is just a wonderful bonus!

---

### Post by SeijiSensei on 2014-01-29
> but it looks like that may not be compatible with Ubuntu 12.04LTS
Is that based on a credible source or just some rumor on the Internet?  I've run a number of Linux distros on a variety of Dell machines, both desktops and servers, for many years now.  I've never had a problem.  What, specifically, is the claimed incompatibility?

You might want to edit the title of this thread to "Recommended desktop machines" so people will not think this is a thread about Ubuntu vs Kubuntu vs Lubuntu vs etc.

---

### Post by archaeometrist on 2014-01-29
The incompatibility is in the video as I remember.  I'd googled "Dell Optiplex 7010 i7 Linux Ubuntu 12.04" and it was one of the links... I think to a blog entry on the Ubuntu One blogs.

The system isn't mentioned in the certification but another version of the 7010 is (with different hardware).  I don't have the time to fuss and fight with video incompatibilities or anything like that - the end of the semester is still three months off.  I want to find something that if loaded with windoze, can be reloaded with Ubuntu and running right away, after I drop the other sound card and a parallel/serial card in it.

---

### Post by deadflowr on 2014-01-29
I think you'll have four different graphics stacks to work with for precise.
While the system might not have been workable for 12.04, it might be workable for 12.04.1, or .2 ,or .3, or upcoming .4.
More here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by SeijiSensei on 2014-01-29
> **archaeometrist said:**
> The incompatibility is in the video as I remember.  I'd googled "Dell Optiplex 7010 i7 Linux Ubuntu 12.04" and it was one of the links... I think to a blog entry on the Ubuntu One blogs.

Well, there is [this post here](http://ubuntuforums.org/showthread.php?t=2193820) about someone with a problem with an NVIDIA card.  However I did a quick search of the 7010's and, like most Dell machines, they usually come equipped with Intel graphics which should not pose a problem for any Linux distribution.  [Here are a few 7010's with Intel graphics that I found at the Outlet store]("http://outlet.us.dell.com/ARBOnlineSales/Online/InventorySearch.aspx?c=us&cs=28&l=en&s=dfb&brandid=2802&fid=9870").

A parallel/serial card, huh?  I just threw away a parallel card the other day seeing as I no longer own any devices that would work with it.  9/25-pin serial connections are pretty much a thing of the past as well.  USB supplanted so much of that stuff.  I also tossed an ancient SCSI adapter card; I don't have any SCSI devices any more either.

---

### Post by archaeometrist on 2014-01-29
I've got some devices I built and use which are controlled by parallel, and my mapping GPS units all use serial (plus other equipment we use also works by parallel or serial).  That's why I need them... and I have a few scuzzy cards laying around (especially a PCMCIA version) - sometimes we encounter stuff with scuzzy interfaces that I bring home to "play with".  When your lab equipment is built to last, sometimes the consumer stuff (computers for instance) outpaces the technology and causes all sorts of strange headaches.

The info for the Dell I'm looking at says HD4000 graphics, but then it also says 1Gb AMD Radeon HD 7570 with VGA, Optiplex, and FH - probably an additional video card installed by the factory and that's probably the conflict.  I haven't had the time to research that.

---

### Post by mastablasta on 2014-01-30
7xxx don't have such good support i belive. though it should work with AMD drivers. then again one can always just turn off the secong GPU and use the intel one that will work. in linux world things change and get updated quite fast.

---

