---
title: "Buying an External HDD..need help."
date: 2008-06-14
forum: General Help
---

### Post by Tom--d on 2008-06-14
I would like to buy this external hdd.

[http://www.dabs.com/productview.aspx?Quicklinx=53MP&CategorySelectedId=11157&PageMode=1&NavigationKey=11157,405460000,47160000,4294955530,397010000](http://www.dabs.com/productview.aspx?Quicklinx=53MP&CategorySelectedId=11157&PageMode=1&NavigationKey=11157,405460000,47160000,4294955530,397010000)

But, does it work with linux?

Is that a reliable hdd?
Also, does it work with the ps3?
What other ones do you recommend.

*has to be 250GB
*has to be around £60
*had to be usb powered
*2.5"

Thanks,
Tom

---

### Post by Rocket2DMn on 2008-06-14
Western Digital external drives (WD Passports) tend to work well with linux.  The biggest problem I see with that drive is that it is 5400rpm and 2MB cache instead of 7200rpm and 8 or 16MB cache.
I don't know about the PS3, but I imagine that it would work just fine.

---

### Post by cybrsaylr on 2008-06-14
Any Ext HDD should work with linux.
I also would go with a 7200rpm and at least 8 or 16MB cache, it will run quicker. I like Seagate drives because of their 5 year warranty.

---

### Post by konungursvia on 2008-06-14
Yes, get a 7200 rpm or faster, and completely format it to ntfs format if you use windows or ps3 with it, or ext3 if you will use only linux.

---

### Post by Tom--d on 2008-06-15
Right I see. 

And why will I need to have 7200rpm? As my hdd is only going to be for backing up and storing films. (they will be played on the ps3)

I can understand the cache to be more as 2mb is low. but im on a low budget

---

### Post by scouser73 on 2008-06-15
There have been one or two issues with Seagate external HDDs for one reason or another.  PC World have a 500GB Maxtor HDD on sale for £59.99 - it's a web exclusive. [http://www.pcworld.co.uk/martprd/product/seo/324729]("http://www.pcworld.co.uk/martprd/product/seo/324729")

I bought one the other week and can recommend it.

---

### Post by yoman82 on 2008-06-15
Most, if not all External Drives will work with Linux. I would upgrade to at the very minimum 4MB cache and 7200 RPM, though. Check this site for good deals: [http://bensbargains.net/category/37](http://bensbargains.net/category/37)
Great deal, I would get this one if I were you: [http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=10005016](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=10005016)

---

### Post by Arlanthir on 2008-06-15
I recently bought a Western Digital 320GB Passport and it works very well. I converted it to ntfs with the _windows_ command:

```
convert X: /fs:ntfs
```
where X is your drive letter assigned by windows.

This converts fat to ntfs, without formatting ;)

---

### Post by Tom--d on 2008-06-15
Thank you for your input :)

What I'm looking for is, (and has to be)

2.5" HDD
USB powered
250gb or more
I have £70 to spend on one.

---

### Post by Tom--d on 2008-06-15
> **Arlanthir said:**
> I recently bought a Western Digital 320GB Passport and it works very well. I converted it to ntfs with the _windows_ command:

```
convert X: /fs:ntfs
```
where X is your drive letter assigned by windows.

This converts fat to ntfs, without formatting ;)

Cool, but I don't have Windows ;)

---

### Post by Arlanthir on 2008-06-15
Oh, in that case I guess the best move is formatting it to ext3 right after buying.

The rest is still true, Western Digital seems to work fine (besides my usual file copy problems, not related to the extern hdd). Ubuntu picked it up automatically and behaves normally.

Good luck with that ;)

---

### Post by Tom--d on 2008-06-15
Thanks :)

mmm.. but, I will (probably, over my friends house use the hdd) what format shall it have it in?

I don't perticatly want ntfs. fat32? (I dont think im going to have 4gb files) maybe 1gb files, thats it.

---

### Post by Arlanthir on 2008-06-15
I had some problems with capitalization + special characters under Ubuntu with fat32, but maybe that's just me... 
Maybe you could give it a try and if it doesn't work perfectly you change the format. As I said, there are ways of converting fat to ntfs without formatting, so you have always a chance to try.

---

### Post by EmanresuusernamE on 2008-06-15
> **Tom--d said:**
> Thanks :)

mmm.. but, I will (probably, over my friends house use the hdd) what format shall it have it in?

I don't perticatly want ntfs. fat32? (I dont think im going to have 4gb files) maybe 1gb files, thats it.

If your friend doesn't have Linux, then you will either need to use FAT32 or NTFS.  If he doesn't have at least 2000, then you'll need to go with FAT32 for sure... Unless he has one of the many programs that allow Win9x and DOS to read NTFS drives.

Or what you could do is partition the drive and have half of it using a windows partition and the other half using a Linux partition.  That way you can put stuff on it that you don't want your friend to see........ That is if he doesn't have Linux at all.

AFAIK, Linux in general will detect any hard drive that Windows can.  One of the neat things about Linux though, it that you can put it on a little jump drive and it won't complain about it at all.  :D  I've got my Ubuntu server on a 4g jump drive right now.

---

### Post by Tom--d on 2008-06-15
mm.. I guess ntfs is really the one I need. 

fat32, i was thinking that. I might go with that first and see what happens. 

and, Jump drive? whats that?

---

### Post by EmanresuusernamE on 2008-08-14
> **Tom--d said:**
> mm.. I guess ntfs is really the one I need. 

fat32, i was thinking that. I might go with that first and see what happens. 

and, Jump drive? whats that?

A Jump Drive is a little USB drive that you can carry around with you.  It's just another name for Thumb Drive.

I forgot to mention, and forgot to check the forums for awhile, FAT32 has a size limit of like 120GB, anything over this will get corrupted sooner or later.  I formatted a 200GB drive using FAT32, which at the time I knew couldn't handle it, but XP did if just fine so I ignored that little though.  Later on the drive started to get corruptions, and I had to keep doing repairs on it.  If you use FAT32, make sure you only use the first 110GB or so, 10GB left out just to be safe.

---

