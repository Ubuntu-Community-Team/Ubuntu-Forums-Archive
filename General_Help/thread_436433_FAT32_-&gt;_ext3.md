---
title: "FAT32 -&gt; ext3?"
date: 2007-05-07
forum: General Help
---

### Post by juxtaposed on 2007-05-07
I have a Acomdata E5 HybridDrive Hi-Speed USB 2.0 HD500UHE5-72 (500GB in storage company terms, a little lower in real terms), and it's all one big FAT32 partition (except for small CD thing that came with it).

And I realised FAT32 wasn't all that great (I can't store DVD Images since theyre over 4GB, and other bad things about an old microsoft patched up filesystem), and I could easily use ext3 in windows. But I have like 200GB of stuff on it, and I don't want to loose it. Any recomendations on how to switch to a better (but still windows compatable filesystem), maybe ext3 or something else? Or, should I even risk messing up something?

My idea was to shrink the FAT32 partition, make an ext3 one after it, copy everything over, then make the ext3 fill the whole drive.

Wikipedia says there is an ext4, should I go for that? What about ReiserFS, or XFS? I know little/nothing about them. I want a minimum chance of data loss (both during the transfer to a new filesystem, and after), as my data is really important to me.

---

### Post by Jeremy23 on 2007-05-07
> My idea was to shrink the FAT32 partition, make an ext3 one after it, copy everything over, then make the ext3 fill the whole drive.

Be aware that you can make an ext3 partition smaller or bigger, but you can't move the starting position of it in the drive.

e.g. if you have a 200GB drive, and the ext3 partition starts at the first 100MB, then you can make it grow to the rest of the drive, but you can't move it to the beginning of the drive and make it occupy the whole 200MB. You have to make it at the beginning of the drive to start with. Sucks, I know, but you can move the starting point of FAT32, though.

> Wikipedia says there is an ext4, should I go for that?

I doubt Ubuntu supports that yet.

> and I could easily use ext3 in windows

You're referring to the "fs-driver.org" thing, right? Well, I had a whole Linux system corrupted by that driver once, be very wary. It's closed source.

---

### Post by Slim Odds on 2007-05-07
> **juxtaposed said:**
> 
My idea was to shrink the FAT32 partition, make an ext3 one after it, copy everything over, then make the ext3 fill the whole drive.

Resizing partitions is **very risky**. If your data is really important to you, back it up somewhere else first. Otherwise, you're just asking for trouble.

---

### Post by rbmorse on 2007-05-07
He should back up the data anyway, whether he ends up doing anything about the partitions or not.

---

### Post by juxtaposed on 2007-05-08
> e.g. if you have a 200GB drive, and the ext3 partition starts at the first 100MB, then you can make it grow to the rest of the drive, but you can't move it to the beginning of the drive and make it occupy the whole 200MB. You have to make it at the beginning of the drive to start with. Sucks, I know, but you can move the starting point of FAT32, though.

Hmmm... Well, could I make the seond partition in ext3, copy everything to it, then make an ext3 partition in the first part (where the FAT32) was, copy everything back, then delete the ext3 on the second half and extend the ext3 on the first half?

> You're referring to the "fs-driver.org" thing, right? 

I think it's like "IIFS" something. Oh, wait, I guess that's the same thing...

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It seemed to work great for me so far.

> If your data is really important to you, back it up somewhere else first.

I'd really love to, but I really don't have any place to back it up to. I have many DVDs, but I think that would be a waste as I don't think DVDs last that long.

> He should back up the data anyway, whether he ends up doing anything about the partitions or not.

To practically do that i'd have to get another hard drive, and I plan on filling this 500GB one up. I wish I could afford that, but I can't.

---

### Post by cotcot on 2007-05-08
> **Jeremy23 said:**
> Be aware that you can make an ext3 partition smaller or bigger, but you can't move the starting position of it in the drive.

e.g. if you have a 200GB drive, and the ext3 partition starts at the first 100MB, then you can make it grow to the rest of the drive, but you can't move it to the beginning of the drive and make it occupy the whole 200MB. You have to make it at the beginning of the drive to start with. Sucks, I know, but you can move the starting point of FAT32, though.



Correction. You can move the start position of a partition to the beginning of the drive. I have done it a couple of times.  The precondition to do that is that the unallocated space before the partition to be moved needs to be larger than the partition to move. Use the Gparted LiveCD for that. (moving is ok as long as there is no overlap; this is clearly mentioned in teh parted manual).

---

### Post by Jeremy23 on 2007-05-08
> **juxtaposed said:**
> Hmmm... Well, could I make the seond partition in ext3, copy everything to it, then make an ext3 partition in the first part (where the FAT32) was, copy everything back, then delete the ext3 on the second half and extend the ext3 on the first half?

That would work, but I'd shrink the FAT32 partition, shift it to the end, and create an ext3 partition at the beginning.

> **juxtaposed said:**
> 
It seemed to work great for me so far.


You just wait until Windows crashes one day, and it'll corrupt your journal. The driver is only designed for ext2, not ext3.

> **juxtaposed said:**
> I'd really love to, but I really don't have any place to back it up to. I have many DVDs, but I think that would be a waste as I don't think DVDs last that long.

To practically do that i'd have to get another hard drive, and I plan on filling this 500GB one up. I wish I could afford that, but I can't.

I have the same problem. I currently have a half-broken Feisty system that is my every-day desktop machine because there's too much on it to back up, and I can't really be without it.

> **cotcot said:**
> Correction. You can move the start position of a partition to the beginning of the drive. I have done it a couple of times.  The precondition to do that is that the unallocated space before the partition to be moved needs to be larger than the partition to move. Use the Gparted LiveCD for that. (moving is ok as long as there is no overlap; this is clearly mentioned in teh parted manual).

Oh, can you? I had no idea. So, what you're saying is that once you've moved an ext3 partition, you can still move it to the beginning of the drive? That would have come in *very handy* about one year ago for me.

---

### Post by milton1 on 2007-05-08
> **cotcot said:**
> Use the Gparted LiveCD...

Gparted live has been my best friend many times. Highly recommended.

---

### Post by cotcot on 2007-05-12
> **Jeremy23 said:**
> 


Oh, can you? I had no idea. So, what you're saying is that once you've moved an ext3 partition, you can still move it to the beginning of the drive? That would have come in *very handy* about one year ago for me.

Yes you can. Be careful if you jump over another partition because then you have to renumber partitions in fstab. The gparted-manual describes with examples how to do that. It is however better not to jump over a m$ partition.

---

