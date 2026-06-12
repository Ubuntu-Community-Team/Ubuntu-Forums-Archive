---
title: "Raid 0 Config...Possible?"
date: 2008-05-26
forum: General Help
---

### Post by jim256 on 2008-05-26
Hey all, 
Ok, so I had Ubuntu on my previous box about a year or so back, and was playing around with 7.04/7.10 and really liked it.

My problem was that I then upgraded to a slightly higher performance pc, one that I configured as Raid0.  I read back then, and have done some reading now, but must say that I feel more than slightly overwhelmed/lost.

My question that I just want to get is...With my current setup, A WinXP Pro SP3 PC, with two 80gb HDD's configured as Raid0 and partitioned as a few different sizes/drives...Can I install Ubuntu using Wubi?

If not, can I install it at all, such as using the method of a live cd (did this a few times before).

Thanks a lot!,
Jim.

p.s. im sorry if this answer is obvious.  I am pretty used to the forum system and am a very active member of a couple boards, but just haven't been able to find the straight answer im looking for just yet.

---

### Post by ago on 2008-05-26
> **jim256 said:**
> 
My question that I just want to get is...With my current setup, A WinXP Pro SP3 PC, with two 80gb HDD's configured as Raid0 and partitioned as a few different sizes/drives...Can I install Ubuntu using Wubi?
Software raids are not supported at the moment and hence Wubi is likely NOT to work

> If not, can I install it at all, such as using the method of a live cd (did this a few times before).
Probably yes but it might be a bit trickier as you will have to install dmraid separately. There should be some guide.

---

### Post by jim256 on 2008-05-26
> **ago said:**
> Software raids are not supported at the moment and hence Wubi is likely NOT to work


Probably yes but it might be a bit trickier as you will have to install dmraid separately. There should be some guide.

hmm ok then :S well any help is appreciated!  i guess ill be searching around for ubuntu dmraid raid install then! thx.

---

### Post by jim256 on 2008-05-26
so another quick question...

seeing as how i would have to install dmraid _after_ (right?) i install ubuntu...what would I want to install ubuntu on initially? just a standard drive, then using dmraid i would somehow later be able to move things around to how i would want them.

im just confused at how this would end up well for me.

thanks.

EDIT: or could i simply go about doing this by running the livecd, then installing dmraid, and THEN installing ubuntu to my raid system...?

---

### Post by ago on 2008-05-26
> **jim256 said:**
> 
EDIT: or could i simply go about doing this by running the livecd, then installing dmraid, and THEN installing ubuntu to my raid system...?

Yes that is what I meant, but you will have to doublecheck that since I am not familiar with dmraid installations myself.

---

### Post by jim256 on 2008-05-26
alrighty, well i gave that a try.  

dmraid was definitely having an effect in that it helped the system to identify raid partitions, but when trying to install (using ext3 as my main partition because after searching I wasn't sure which was best and was compatible with windows...) i received this error after finally getting past everything else:

The ext3 file system creation in partition #4 of Serial ATA RAID pdc_jgabeiii (stripe) failed.

any ideas anyone? 

Thanks a lot, Jim.

---

### Post by ago on 2008-05-26
I will forward to the dev in charge

---

### Post by jim256 on 2008-06-03
> **ago said:**
> I will forward to the dev in charge

well, unfortunately I (for the 1000th time) blew away my xp partition, and spent a few days with acronis trying to recover to no avail.  im now back up and running, and wanted to thank you for your great suggestions, as well as the forwarding of those errors to the head dev of whichever department.

thx, ill keep trying! (after backing up ;) )

---

