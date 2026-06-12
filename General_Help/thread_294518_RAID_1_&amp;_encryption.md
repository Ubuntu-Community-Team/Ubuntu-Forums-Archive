---
title: "RAID 1 &amp; encryption"
date: 2006-11-06
forum: General Help
---

### Post by felixj on 2006-11-06
Since I have a lot of rather sensitive data on my HD I want to build an encrypted RAID-system. I haven't done a lot of research on this, so I would be grateful for some hints. 

1. I need a controller card. I'm planing to buy a S-ATA-PCI-Controller with RAID abilities (like [this]("http://cgi.ebay.com/NEW-4-CHANNEL-SATA-RAID-PCI-CONTROLLER-W-SILICON-IMAGE_W0QQitemZ170044737834QQihZ007QQcategoryZ39968QQrdZ1QQcmdZViewItem"))
Are there any compatibility-issues or something else I should be aware of?

2. My setup is gonna look like this:
1*80GB drive for the system & home partitions
2*250GB RAID
What are the steps needed after I installed ubuntu on the system drive? I could figure out how to set up a RAID system using the existing howtos, but how do I set up an encrypted RAID? I want to have a completely redundant RAID 1.

Thanks for any tips,
felixj

---

### Post by kidders on 2006-11-06
Hi there,

I'm quite happily using distributed (with AoE) software RAID with dmcrypt atm. I'm not really expert enough to have an opinion about how "good" it is, but I can't say I have any complaints.

dmcrypt isn't your *only* option, but it seems sensible enough to me :-) I've also played with EncFS a bit.

There are plenty of dmcrypt-related HOWTOs around. You *should* be able to almost ignore the fact that yours will be sitting on a RAID array, when you're following them. Personally, I opted for a configuration that requires a USB key to be plugged in during boot, for the filesystem to decrypt successfully. It gives me an added sense of security, should my boxes ever get stolen.

I have two questions though:

[LIST]
[*]How come you've decided to buy a hardware RAID controller? IMO software RAID is safer ... unless of course you're avoiding it for a reason :-)
[*]Encrypting RAID can be a bit dangerous if your power supply is any way unreliable. If both your hard disks were to go offline simultaneously, an encrypted filesystem will almost always suffer _much_ more damage than an unencrypted one. I wonder if your money would be better spent on a UPS.
[/LIST]

---

### Post by felixj on 2006-11-08
Thanks for your reply, some new ideas for me to think about.

I haven't heard of AoE before (but found out it means ATA over Ethernet). Sounds interesting. What hardware do I need? Can you get small boxes for S-ATA disks that have ethernet and just plug them to the network?

I have my harddrives encrypted right now, so I know something about dmcrypt. Problem is: I'm running out of diskspace and I figured looking at the prices of HDs that it would be easier to use another HD for backup (Currently I make unencrypted backup DVDs and keep them at a friend's place, which is starting to get on my nerves). The solution I came up with so far is a RAID 1-system. I have to buy a S-ATA-controller anyway (so far I have only IDE) and they usually come with RAID-abilities. Having two completely redundand disks sounded like the safest thing, but as you see, I don't know much about the alternatives.

>     * How come you've decided to buy a hardware RAID controller? IMO software RAID is safer ... unless of course you're avoiding it for a reason
    * Encrypting RAID can be a bit dangerous if your power supply is any way unreliable. If both your hard disks were to go offline simultaneously, an encrypted filesystem will almost always suffer much more damage than an unencrypted one. I wonder if your money would be better spent on a UPS.

Why is software-RAID safer? I figured since I have to buy a controller anyway it would be best to let the hardware do the job.

I found out that UPS is „Uninterruptible Power Source“. My power supply is just normal household elictricity, so we have blackouts once in a while. But buying an UPS is a little out of my financial reach. So is there any other solution to this? 

The files on the disk will not change very much, so a backup twice a day would be sufficient. So maybe I just install one encrypted 250GB disk and run a backup twice a day to another disk. Is there an easy way to do this for encrypted file systems?

Thanks for helping me in the orientation process.
felixj

---

### Post by kidders on 2006-11-08
Hey again,

> **felixj said:**
> Why is software-RAID safer?
The idea behind RAID is redundancy. If you set up RAID that's implemented in hardware, your entire array will only be available as long as that hardware is working. If it should break, you're data would be inaccessible until you could find a replacement ... assuming the controller is still being sold by that time. With software RAID, on the other hand, the only hardware you'd be relying on is the PC itself. If it failed, you would simply plug the array into another one and carry on.

Most modern hard disk controllers with built-in RAID capabilities _are_ software RAID anyhow. I suspect you may be buying one of these, since you mentioned that a UPS (which should only cost about &#8364;100) is out of your price range. In that case, you would be getting none of the advantages of a hardware RAID controller, which are ...
[LIST]
[*]Easy hot-swappability
[*]Blinding speed
[/LIST]
... and exposing yourself to significant disadvantages (when compared to Linux's software RAID implementation), ie ...
[LIST]
[*]Very infrequent software updates/bug fixes
[*]Total reliance on hardware that may become unavailable in the future
[/LIST]
The whole issue is very complex really ... but I've tried to provide as good a summary as I can. I have always felt that my data is safer with kernel/user level RAID because, not matter what happens, the same array will work indefinitely (and reliably) in any computer, regardless of the architecture ... all I need to do is plug it in.

> **felixj said:**
> I haven't heard of AoE before
I've never tried to use it until relatively recently. Tbh, I like the idea of having at least part of a RAID 1 array in a separate computer. Technically, doing so probably doubles the risk of failure (by doubling the number of CPUs, PSUs, etc. that could blow up hehe), but correspondingly reduces the risk of actual data loss. Again, I've implemeted AoE in software, using vblade and aoetools, and am pleased (without being overjoyed) with performance. Of course, since you mentioned your data is relatively infrequently modified, you should see a net performance gain, since most disk accesses will be reads.

> **felixj said:**
> Can you get small boxes for S-ATA disks that have ethernet and just plug them to the network?
Yes, but bear in mind that your ethernet cable will be a *serious* bottleneck. If you'll be doing lots of writing, you may have to find faster networking alternatives.

> **felixj said:**
> Having two completely redundand disks sounded like the safest thing, but as you see, I don't know much about the alternatives.
Well, each version of RAID has its own advantages. Version 1 gives very good read performance, but writing is a killer, since every member device is involved in doing it. It's also quite failure resistant, in that you (obviously) only need one clean copy of your data to reconstruct an entire array.

Something to bear in mind when reading about RAID performance is that, when it's implemented in Linux, or by ATA hardware with RAID "capabilities" (which still means software), bus contention is a major issue. For instance, my motherboard supports 4 IDE and 4 SATA hard disks. If I were to use them all at the same time, huge queues would develop at my I/O buses. So, depending on the RAID version I chose, I would have to revise down my performance expectations, based on a little knowledge of how various I/O operations are actually performed. Read/write speeds quoted on forums/etc. for each RAID version tend to assume you've bought very expensive hardware that can operate much closer to the theoretical maximum speeds.

> **felixj said:**
> Buying an UPS is a little out of my financial reach. So is there any other solution to this?
No, not really. To be honest, I don't think I could (in good conscience) store *really* critical data on disks that aren't protected by a UPS. In real terms, to have a problem, the following would have to happen simultaneously:
[LIST]
[*]I'd have to be writing to the array.
[*]I'd have to be performing a write that the particular filesystem I chose was weak at.
[*]The power would have to fail.
[/LIST]
Then, depending on the specific filesystem, I'd either lose my changes (transactional filesystems), lose the filesystem journal (which would be okay), leave the filesystem inconsistent (which could be quite bad), or all of the above. If the filesystem were an encrypted one, even a minor inconsistency that could not be corrected would be very serious, and could destroy large amounts of data.

The UPS I'm using at the moment gives me 10-15 minutes of running time, when the power fails, at a cost of about &#8364;100. Essentially, all it does is give an automated shutdown a chance to happen cleanly, guaranteeing the safety of my data, no matter what was being done to it at the time.

I hope some of this is helpful :-)

---

### Post by Mujaheiden on 2006-12-08
With encfs files are encrypted seperately. In case of data loss due to power disruption, chances are you'd only lose one file, right? 

Im setting up my email all secure, but it seemed rather senseless to have the  thunderbird local folders in an unprotected partition. Our government has this thing about tapping.
On the other hand, i wouldn't like to risk for the sake of privacy one single bitflip destroying all my email data - which could be the case with an all-encrypted volume, if I'm not mistaking.

The solution would be RAID - is this also possible between partitions on two seperate disks? - or an encfs-kind of encryption.

On such a file system where files are encrypted seperately, would raid still be wise? I mean, I don't mind losing one folder, I might just have backups - but I do mind losing all.

---

