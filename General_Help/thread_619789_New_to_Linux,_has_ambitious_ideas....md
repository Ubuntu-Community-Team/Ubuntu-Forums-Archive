---
title: "New to Linux, has ambitious ideas..."
date: 2007-11-21
forum: General Help
---

### Post by DigitalNinja on 2007-11-21
Hey there!

I'm just getting into the whole linux thing and unbuntu seems to be the right place to start.  
What I want is to build a multimedia PC that I can access from school, and record TV/ use it has a web server. Anyway heres the components

AMD 5600+
ASUS M2N-sli
Up to 4GB of ram (going to start off with 1)

I need to get a video card, I don't want anything to expensive, something with HDMI would be great but I want it around 100 dollors.  I also need a TV capture card with HD capabilities on it.

Should I use the server or desktop version of this?  Also I don't know how to install programs or anything onto it.  Step by step instructions would be nice, or just pointing me in the right direction.

I have a belkin G wireless card is this compatible?  I also have a ATI theatre 550 is this TV card compatible?

Anyway thanks guys!

---

### Post by zach12 on 2007-11-21
Have a look at mythtv

---

### Post by rmemm on 2007-11-21
I have a PCHDTV ([http://www.pchdtv.com/](http://www.pchdtv.com/)) HD and Composite Frame Grabber.  The HD-5500.  I'm still setting it up but it's suppose to be for linux.  

For video cards -- you can try the ATI -- but nVidea is what Mythtv recommends.  There are some specific decoding features recommended.  I'd go the the Mythtv site and read a bit.  Essentially you need Xv and XvMC support and for TvTime you need YUY2 support which maybe only comes on some nvidia cards.  Maybe others know -- though AMD/ATI are improving their drivers -- so they might work.

By the way -- for non-hd pretty much anything kind of works.  I have a Pentium II 300 and an old video car without video acceleration and it sort of works for old style tv and small screen sizes.  HD -- mostly does not work.

For networking it's really best to go hard wired for video -- though in principle a high speed wireless link might work -- but you need something more than 10 MB/s I think if your doing HD.  I don't know how much -- but people say 100TX is enough.  That's why I say a very solid high speed wireless might be enough--but only might.

If your going to use this as a video server -- you might want to think about power consuption.  There are choices in the AMD line to buy a 65W CPU vs. a 80, 90, 125W etc.  You can also get an 80% efficient power supply not a standard one, and video card choice effects power a lot.  Low power is 24W or even lower, some are 80W or more.  I mention this because a video server might be on quite a lot.

Rob

---

