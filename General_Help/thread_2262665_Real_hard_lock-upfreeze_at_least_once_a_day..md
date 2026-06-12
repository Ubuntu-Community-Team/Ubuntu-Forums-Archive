---
title: "Real hard lock-up/freeze at least once a day."
date: 2015-01-26
forum: General Help
---

### Post by warren3 on 2015-01-26
Hi.

Well I am in a bit of bother with Ubuntu.  I jumped on the Ubuntu bangwagon about 2 months ago sold my Windows system recently meaning I am solely a Ubuntu user now.  It seemed like a good idea at the time and I do really like Ubuntu but my system is not happy at the moment.

What happens is I get a hard lock-up / system freeze at least once a day that requires me to push the power button till it turns off because nothing will reset it (REISUB etc. doesn't work).  My wireless keyboard and mouse lock up as well.

I have the following:

Gigabyte Brix i3 4010U (This runs a 4400 Intel Graphics chipset and ultrabook i3 processor.  I bought this as an open box off ebay so I could be faulty?)
Crucial mSata M500 SSD (This could be the issue as I have since read of a Queued-Trim data corruption problem on this drive that affect Linux users, although digging deeper on the matter it seems my kernel should not be affected)
Intel 7260 Wifi adapter (I thought this could be the problem but I removed it and used a TPLINK USB WIFI stick and I got a hard freeze as well)
8GB Crucial 1600Mhz DDDR3L RAM (I have done a quick memtest86 for about 2 hours and it passed although it could do with a full night of testing)

I am running 14.04.01 LTS with latest kernel.

If you would like some kernel log info then please ask and I will gladly post it.  I can see in the log were the hard freeze happens but have no idea what all the system code means.

I will be glad for any assistance as I am desperate for a stable Ubuntu machine.

---

### Post by tgalati4 on 2015-01-27
Yes, I'm guessing you have a faulty motherboard.  Static electricity damage or damage while installing cards or shorting something out while assembling.  Open box and ebay is not a good combination.  Check the power supply with a voltmeter, but otherwise, I'm leaning towards a bad motherboard.

---

### Post by warren3 on 2015-01-27
Hi.

Oh no that is not a good diagnosis.  It was a good price, perhaps a little too cheap.  Maybe I should have erred on the side of caution.  Strange thing though is that I am sure it was ok with Windows 7 for a short while I had that installed.  If I install Windows 7 again and don't get the same problem can I rule out the MOBO?

---

### Post by warren3 on 2015-02-11
I fixed it!

It was the power brick.  I replaced it and its working fine.  No lock ups.  So your suggestion about the power supply was spot on.

Cheers.

---

### Post by tgalati4 on 2015-02-12
Glad you got it fixed.  You should have a better Linux experience from now on.  Enjoy your new freedom.  Leave a feedback comment for the ebay seller.  Perhaps you will get some compensation for the bad power supply.  Buying anything open box from ebay is risky; you were lucky in this instance.

---

### Post by warren3 on 2015-02-14
Cheers.

It was really souring my Ubuntu experience I can tell you that!  I was ready to ditch it and go back to Windows!

The seller has been good.  He sent out a replacement supply from a Celeron Brix but unfortunately the power output is wrong.  It seems the i3 is more power hungry.  I have sent him a message and hopefully he can come good with a power supply that is right this time.

---

