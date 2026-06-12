---
title: "Do you have Ubuntu + LUKS on a SSD hard drive?"
date: 2013-04-01
forum: General Help
---

### Post by vcrpcant on 2013-04-01
I would like to buy a SSD hard drive and install ubuntu + LUKS on it.
But first I'd like to hear the advices from someone who has already done it.

I only use this programs:
- firefox
- openoffice
- virtualbox (with some wxp and w7 guests)

---

### Post by haqking on 2013-04-01
> **vcrpcant said:**
> I would like to buy a SSD hard drive and install ubuntu + LUKS on it.
But first I'd like to hear the advices from someone who has already done it.

I only use this programs:
- firefox
- openoffice
- virtualbox (with some wxp and w7 guests)

Advice on what ?

I have Fedora and Slackware on SSD with LUKS, what is your particular concern or question regarding Ubuntu ?

---

### Post by vcrpcant on 2013-04-01
> **haqking said:**
> Advice on what ?

I have Fedora and Slackware on SSD with LUKS, what is your particular concern or question regarding Ubuntu ?

Well, I just want to know if there is any danger of data corruption, because I've read somewhere that SSD drives have write limits (sorry for not being able to explain im more detail). 

That, in conjunction with LUKS and virtualbox makes me think twice before jump into SSD scene.. :(

---

### Post by haqking on 2013-04-01
> **vcrpcant said:**
> Well, I just want to know if there is any danger of data corruption, because I've read somewhere that SSD drives have write limits (sorry for not being able to explain im more detail). 

That, in conjunction with LUKS and virtualbox makes me think twice before jump into SSD scene.. :(

People say the same thing about USB flash drives, I have one from about 10 years ago which has gone through the washing machine twice and still works fine ;)

You will be fine, no concerns IMO, you will want to look at SSD optimisation though with things such as noatime and TRIM.

Here is a primer to get you off on the right foot to ask specific questions once you have one etc [http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm](http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm)

I use 2 SSD in my main system, one for multiple OS and one for backups and I use a 3 x 2TB HDD for data storage (primarily as the larger size mechanical HDD are cheaper)

My system is on 24/7

There are no issues IMO.

Enjoy

---

### Post by Paqman on 2013-04-01
> **vcrpcant said:**
> I've read somewhere that SSD drives have write limits(

They do, but in practical terms so do old-fashioned spinning drives. No drive will last forever, but SSDs do have wear-levelling algorithms that ensure that the drive doesn't write to the same spot too often and wear it out. Many people (including myself) have been working SSDs hard for years now, they've proven to be at least as reliable as spinning drives (probably considerably more so in fact).

In short, don't worry about it. Carry out some of the optimisations alluded to above to improve performance, but limited writes isn't something to worry about unless you have one of the ropey old first generation drives such as those in the early Eee PCs.

---

### Post by vcrpcant on 2013-04-02
Thank you both very much :) 

That kind of information and first hand experience was what I exactly what I was looking for!

Best regards

---

