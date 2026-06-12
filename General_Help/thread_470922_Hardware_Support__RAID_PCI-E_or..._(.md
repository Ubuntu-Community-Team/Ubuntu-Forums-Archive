---
title: "Hardware Support / RAID PCI-E or... :("
date: 2007-06-11
forum: General Help
---

### Post by Draco355 on 2007-06-11
Rather new to the forums, but I'll explain quickly what I've done so far. :)

I decided to build a little DVR/Security machine to record camera's w/ Zoneminder. I got an Intel DQ965GF  with a Core2Duo E6420 that was an absolute nightmare for me, SATA and IDE controller-wise, but I'm happy to report that Ubuntu 7.04 found the controller just fine out of most of the distro's. (The **Intel DQ965GF**: [http://www.newegg.com/Product/Product.asp?Item=N82E16813121057](http://www.newegg.com/Product/Product.asp?Item=N82E16813121057) ) It's just that the e1000 driver hangs the machine on booting for random amounts of time. (something with e1000_request_irq and a Unable to allocate MSI interrupt - error -22) and I had to fall back to software RAID to do any sort of RAID1. Seemed rather finicky, I'm just not that comfortable with it.

Either way, I don't care much for FakeRAID (as I recently learned that the Intel board pretty much does), so I need to get a board that just isn't as new either.

I'm looking at this Biostar: [http://www.newegg.com/Product/Product.asp?item=N82E16813138043](http://www.newegg.com/Product/Product.asp?item=N82E16813138043) 
This has - again - onboard SATA RAID... which I hope isn't fakeraid. Also, maybe this time the IDE channels won't be controlled by the 3rd party chip.

- Does anyone have any experience with this Biostar board? (**P4M890-M7**)
- If SATA RAID 1 isn't worth the time w/ the Biostar, is the Adaptec 2240900-R 1430SA worth grabbing to take care of that? (I'm only doing SATA RAID1)

Any advice or help on this would be great. I hope this is going into the right forum, since I didn't see any General Hardware help sections that didn't look Laptop-oriented. :)

---

### Post by Draco355 on 2007-06-13
Eh, guess no one has experience with these boards then. :(

Anyhow, if anyone could suggest or point me to a list of RAID cards that properly function (read: show two drives as one device) properly, I'm all ears. :)

---

### Post by houstonbofh on 2007-07-16
A good hint is price.  All of the real RAID cards I have seen start at $200 and go up.  Tom's Hardware Guide is doing a multi-part review of RAID now.  It is Windows oriented, but still good info.  The fast ones won't be fakeraid.

---

### Post by andrewwk on 2007-07-26
Greetings Draco355,

I recently purchased a DG965WH with a core 2 duo.  I came across the fake raid problem, too.  The way I got around it was a [3ware 9650SE-4LPML]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042") to do a Raid 10.  It was extremely easy to install.  The only problem is that there is no specific drivers for ubuntu 7.04.  There is for ubuntu 6 versions.  The drivers are needed are to do a hot swap and light LEDs up.  I hope this helps.

WK

---

### Post by fjgaude on 2007-08-05
Just noticed this. All the late model MBs that have up to six SATA drive controllers working off the PCI-E bus are as fast as it gets. A board like the ASUS M2N32 is one of them.

Correct me if I'm wrong, the PCI-X bus is eight times faster than the PCI, and the PCI-E is 16 times faster. With software raid and 3X raid5 and the latest technology drives I get 114MB/sec read thru-put. It's that low because of my PCI bus. It would be about 140MB/sec if on a PCI-E bus.

When you think an MB  like this costs only $159.00 and a four-port Highpoint RAID controller, like the 2310, also costs $159.00, maybe it's time to upgrade. <smile>

Ran across a fellow using one of the M2Ns and was getting 270MB/sec read thru-put with software 5X  raid5, the Linux md kind, controlled with mdadm.

Just passing thoughts.

frank

---

### Post by bikeman1 on 2007-08-24
draco -- I suggest that "onboard raid" will not be true hardware raid (buffered) plus there are so many different RAID chips that software support is a real problem.  I am betting you have tio be lucky to get one to work.  I set up software raid on one of these once and had nothing but headaches.  

If you go the raid card route, different story.  I suggest 3ware cards because in recent 2.6 kernels, the native driver in linux will support them without any new software.  They are a little pricy, but arguably worth the money for that.  There are cards all the way from 2-drive PCI units to 16-drive PCIx, in order of increasing cost.  I have the 9550SX (PCI) and 9650SE (PCIx4) units and both work great.  It is more complicated to boot onto the raids, software needed.  No I don't own their stock!  But they work very robustly and 3ware also has very responsive support, by email or phone.  Worth the $$

bikeman1:guitar:

---

