---
title: "Where to download Ubuntu Source Code without Apt-Get?"
date: 2007-01-09
forum: General Help
---

### Post by TwistedLincoln on 2007-01-09
I am attempting to locate the full source for Ubutnu 6.10 (edgy).  While the download page for the binary isos suggests that I can get the source at  [http://archive.ubuntu.com](http://archive.ubuntu.com), the archive does not appear to have the full source (I find it somewhat hard to believe that the entire source code for edgy is only 286k).  

While it would be nice to have an source iso image to download, I am willing to download the invididual package sources if needed.  Does anyone have a link to where to get them?

I know I can get the source code via apt-get, but there are two problems with that approach:

1) It principle, it is contradictory: how can one modify the source code to make Ubuntu run on correctly on their hardware, if you must already have Ubuntu installed before being able to get the source?

2) How can one appropriately redistribute Ubuntu without having access to the full source of everything available on the install CD?  I'd like to be able to give out pre-made discs, but want to give out corresponding source CDs as well.

I would greatly appreciate any assistance anyone here can provide.

---

### Post by mcduck on 2007-01-09
You can get both packages & source code from [http://packages.ubuntu.com]("http://packages.ubuntu.com").

But there isn't any single package containing sources for *everything*.

---

### Post by TwistedLincoln on 2007-01-09
Well that's a step in the right direction.  Unfortunately, it does not appear that there is a way to download every package from the same page, so download-assist tools like Flash-Get won't do much good...

I suppose I could just spend hours upon hours downloading each and every file, one at a time...

Honestly, I'd much rather just buy a source CD directly from Ubuntu.  I can't seem to find the "written offer for source code" anywhere on the main Ubuntu site -- is it on the Ubuntu CD?  

I know you can arrange for source code CDs for 6.06LTS if you ordered a disc from ShipIt, but I need the source for 6.10...

---

### Post by mcduck on 2007-01-11
I can't really imagine a reason why you would want to download sources for _all_ packages. It would take ages to compile the thing, and you wouldn't get any benefits from compiling most of the stuff yourself. Anyway, there's Gentoo for those who like compiling things ;)

If you have some hardware problems you only want to compile the kernel.

---

### Post by TwistedLincoln on 2007-01-15
I want to download the sources for all packages because in order for me to comply with the GPL, I have to either provide the source code when I distribute it, or give a written offer that states that I will provide source code by mail if requested.

Although I realize that I could just give out Ubuntu with the written offer, knowing that almost everyone will just get the source files they need using Apt-Get, in the off chance that someone asks, I want to be sure I have a full copy of the source on hand to give them...

I really wonder why Ubuntu makes this so difficult.  Distros like Fedora simply have source isos available, so distribution according to the GPL is easy.

---

### Post by bodhi.zazen on 2007-01-15
> **TwistedLincoln said:**
> I want to download the sources for all packages because in order for me to comply with the GPL, I have to either provide the source code when I distribute it, or give a written offer that states that I will provide source code by mail if requested.

Although I realize that I could just give out Ubuntu with the written offer, knowing that almost everyone will just get the source files they need using Apt-Get, in the off chance that someone asks, I want to be sure I have a full copy of the source on hand to give them...

I really wonder why Ubuntu makes this so difficult.  Distros like Fedora simply have source isos available, so distribution according to the GPL is easy.

Off topic: Where can I download your distro ? I would like to take it for a spin, I won't ask you for the source code or anything like that, just take it for a drive.... ;)

---

### Post by TwistedLincoln on 2007-01-15
I'm glad you're interested.  But actually, it isn't finished yet.  I'm just getting a jump on things, especially considering I figure it might be hard to find the complete source code once the next version of Ubuntu comes out...

I'll send you a PM when it's all done.

In the meantime, in an attempt to promote Linux in general, I'd like to pre-load the unmodified Ubuntu on some laptops I'm selling on eBay.  So I still need the source to comply with the GPL... :)

---

### Post by bodhi.zazen on 2007-01-15
Sure, 

Have partition, will test :p

---

### Post by deanlinkous on 2007-01-15
They use to have source ISOs available. Not surprising anymore though.

Ubuntu ShipIt CDs have the written offer on the cd case and you would just pass on the written offer and it would be up to Ubuntu to provide the source in that case.

If you download then make a physical copy then you probably *should* provide source code as well. Probably easiest way would be a script to read the package list and download source for those and then roll it into a iso or something...

edit - how about....
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.06/release.1/source/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.06/release.1/source/)

---

### Post by TwistedLincoln on 2007-01-16
That's a start.  I suppose I could always just use 6.06.1 instead of 6.10...  

As for passing on the written offer, you can only do that if you are giving away copies-- If I'm loading it onto a system I'm selling, I imagine that qualifies as commercial use, so I don't think I can just pass along the original offer.

I'm going to email Canonical to see if I can order the source for 6.10 from them.  I willl post back here when I get a response.

---

### Post by deanlinkous on 2007-01-16
sorry, didn't realize you were talking about 6.10....

Strange no ISOs....

how about
[http://cdimage.ubuntu.com/daily/current/source](http://cdimage.ubuntu.com/daily/current/source)

---

### Post by TwistedLincoln on 2007-01-17
That's exactly what I was looking for!

Not really easy to find...

Thanks a bunch!

---

