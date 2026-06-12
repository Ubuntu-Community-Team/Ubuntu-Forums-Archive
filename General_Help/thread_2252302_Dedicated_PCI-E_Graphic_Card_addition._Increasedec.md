---
title: "Dedicated PCI-E Graphic Card addition. Increase/decrease system longevity?"
date: 2014-11-10
forum: General Help
---

### Post by mikodo on 2014-11-10
Hi.

 I don't know the answer. What do you think?
 
 This has been my only computer, and it needs upgrades. I don't want to lesson it's longevity.
 
 I plan to increase RAM, add a SSD and a new HDD. I am thinking about updating the graphics, too.
 
 I don't have great video needs. I don't game. I don't do video editing. I don't use it to watch any great video intensive movies and the like. Would upgrading to a dedicated video card, enhance the system's video performance much? It is a PCI Express 1.1 board. [See summary of PCIe 1.1]("http://www.trentonsystems.com/applications/pci-express-interface"). Or, would it be a bottleneck for my system anyway, and possibly put the system under a greater strain, it doesn't need?
 
 [Computer]("http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c01230545-2%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1415566867690.876444892.492883150").
 
 [Motherboard]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c01077641").
 
 [The Temps, remain low.]("http://paste.ubuntu.com/8930963/") The temp sensor reading was after startup but, it remains reasonable with use.
 
 [The PCI-E card]("http://www.zotac.com/us/products/graphics-cards/geforce-600-series/gt-610/product/gt-610/detail/geforce-gt-610-zone-edition/sort/starttime/order/DESC/amount/10/section/specifications.html") I am thinking of adding.
 
 Thank you.

---

### Post by WinEunuchs2Unix on 2014-11-10
It has a SATA II hard drive and if the controller is a SATA II you would be throttling an SSD that can read at 540 MB/s.  SATA II has limits of 300 MB/s or so.

Consider the MoBo chipset which from your 2007 model to today's 2014 has dramatic speed improvements in FSB, RAM speed, not to mention USB 3.0 versus your 2.0 or 1.1 or whatever you have.

I would just sell your $20 PC and buy a new one (even if a used one a couple years old).

PCI-e is a good point you raise and now new SATAe drives and PCI-e SSD drives (my platform supports neither) has speeds of 12 Gb/s or more compared to SATA II's 3 Gb/s and SATA III's 6 Gb/s.

GB=Gigabyte, Gb=Gigabit.

Just some quick thoughts, not too much delving on the subject.

---

### Post by rbmorse on 2014-11-10
The video card won't make much difference to the motherboard unless it really generates a lot of heat (and the one you selected won't). It will demand a bit more of the power supply, as will additional RAM, but that's a consumable component anyway and easy to change when it needs replacing. 

For your stated purposes, performance-wise the nVidia 610 chipset should be fine, especially since you're starting from such a low performance baseline. 

Speaking in general terms, the engineered lifespan for consumer grade electronics like a PC is somewhere between five and eight years.  That doesn't mean it won't continue to work beyond that...possibly many years beyond that, but your system is approaching the end of it's design service life.  Rather than putting money into this soon to be dinosaur it might be more practical to begin setting money aside toward a new system.

---

### Post by mikodo on 2014-11-10
Thank you, for the responses.

I think I will consider not updating too much, given your thoughtful advice.

I have an unused, new HDD, that I bought a couple of years ago, (at about twice the price of one today), that I will stick in this machine. The current HDD, is failing.

This has been a good machine, and may continue to work reasonably well for a while, for my modest needs, (but yes, it may not too).. If it doesn't well, the money not spent on upgrading it, can be used towards a new machine. This sounds like the more sensible approach.

Again; Thank you, for sharing your insights.

My best.

---

### Post by pqwoerituytrueiwoq on 2014-11-11
a gt 610 is a rebranded gt 520, they are they same part with a different label, just so you know
based on what you said i doubt the integrated intel graphics are not enough for you, if you need more try the latest linux kernel

usually the 1st thing to go bad is a PSU or cmos battery
these are my usually goto PSUs for basic systems [http://tinyurl.com/m9h9leu](http://tinyurl.com/m9h9leu)
you can open up your PSU and see if capacitors are bulging/leaking, if they are it is time to replace it

if you feel you need a upgrade over performance i would suggest replacing the mobo/ram/cpu with a intel Pentium (1150 socket) and a 2gb ram stick, that would cost about 120-140 in the us
it is not worth upgrading ram/cpu in such a old system where parts are not very common and have a mark up due to availability

---

### Post by mikodo on 2014-11-11
@ pqwoerituytrueiwoq. Thank you, too!

Yes, I think the cmos battery may be failing. I need to reset the time in the BIOS and on the Desktops, regularly now. EDIT: I read later, that it could be the PSU, not functioning well, that can cause the time setting failures, (not sure how though). So, I will need to check that too! 

I'll take the rest of what you said, into consideration, also.

Of course, my data is backed up, if something does happen. (on an external HD, that is only started, about on average once per week for the quick backups).

Kind Regards.

---

