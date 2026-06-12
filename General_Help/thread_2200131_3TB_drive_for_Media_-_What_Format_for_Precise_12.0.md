---
title: "3TB drive for Media - What Format for Precise 12.04 and WIN XP?"
date: 2014-01-17
forum: General Help
---

### Post by 777funk on 2014-01-17
I'd like to have all my document folders in both WinXP and Ubuntu 12.04 point to partition(s) on my new Western Digital 3TB Red HDD. What's the best solution for doing this? 

These are both 32 bit OS's by the way.

Edit: this won't be the boot drive btw, just media storage.

---

### Post by whitesmith on 2014-01-17
Windows can't process any Linux partitions (ext2-3-4). Linux can process NTFS partitions.

---

### Post by oldfred on 2014-01-17
Also a 3TB drive must be formatted with gpt partitions to use entire 3TB. But XP does not work with gpt partitioning. 
You can partition with MBR but then only have 2TiB.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

    
       GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by 1clue on 2014-01-17
This can't be the boot drive with XP running on the bare metal, unless you're happy with it being a 2T drive and never get the remaining terabyte.

But you could format GPT the way oldfred says, and then install XP as a guest operating system in a VM.  At that point you can share all you want.

---

### Post by 777funk on 2014-01-17
this won't be the boot drive btw, just media storage. I'd like to keep my existing XP install intact (too much software/hardware that isn't Linux compatible) and would also like to keep Ubuntu intact (better for regular use and runs faster).

---

### Post by 777funk on 2014-01-17
By the way I did a format in GParted to NFTS and split it to 2TB and 1TB (approx) and windows sees only 749 or something to that effect and says it's not formatted.

---

### Post by 1clue on 2014-01-17
Here's what Microsoft says about it.

[http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx)

I'm not sure if GPT support can be had for a 32-bit XP, although XP 64-bit is in the list.

I didn't read the entire page, but it seems in line with everything else I've read about GPT and MBR.  What they don't mention is how embarrassed Microsoft should be about this.  MBR partitions (the way XP formats the disk) were obsolete when hard disks reached capacities of 32 megabytes.  Yes, megabytes.  They've been hacked a couple times to "keep up with the hardware" but really IMO there's absolutely no legitimate reason for MBR partitions to even exist today.

---

### Post by 777funk on 2014-01-18
I did a format in GParted to NFTS and split it to 2TB and 1TB (approx)  and windows sees only 749 or something to that effect and says it's not  formatted. I wonder why this isn't working since I have it as less than the 2.2TB it accepts.

---

### Post by 1clue on 2014-01-18
There are no happy solutions for you with the scenario you've given us.

Take another look at that link I sent in post 7.

It says Windows XP 32 bit does not support GPT partitions, so it thinks you have a blank disk.

MBR partitions cannot see more than 2T of any disk.  Not talking about partitions, it can't see more than 2T of the DISK.

There's nothing you can do to make use of all 3T and still have support for 32-bit XP to natively read that disk.

It's not a partition format problem.  It's a drive partition **table** format problem, or rather Microsoft dragging their feet by 20 years, putting patches on patches rather than change to something that works right.

You can do one of these things, but not both:
[LIST=1]
[*]Install GPT partition table(which supports 128 'primary' partitions and a ridiculous amount of total drive space) and make use of all 3 TB with your Linux box (but XP will not see any partitions at all, ever)
[*]Install MBR partition table(which supports 4 partitions and absolutely no more than 2T disk space) and make use of 2T total, and use it with both Linux and XP.  The last terabyte will be inaccessible from EVERY operating system.
[/LIST]

What you COULD do is format GPT, run Linux on the bare metal and then run XP in a VM.

Another thing you could do is buy a 2T drive and format it as MBR which would let you use your drive as you are hoping without wasting any space.

---

### Post by carl4926 on 2014-01-18
Isn't XP about to lick the dust?

---

### Post by 1clue on 2014-01-18
That's a surprise.  I thought XP had reached end of support about 3 years ago.  Instead it's gonna be April.

[http://www.microsoft.com/en-us/windows/enterprise/endofsupport.aspx](http://www.microsoft.com/en-us/windows/enterprise/endofsupport.aspx)

That doesn't mean people won't still be using it.

---

### Post by 777funk on 2014-01-18
Carl49: I still use XP all the time and don't think that'll change for me. I had Windows 7 on my wifes computer (came that way) and it ran slow as molasses. XP runs great. Ubuntu would work even better but for some software (UPS Worldship, Quickbooks, etc) Linux isn't supported so it's not an option. That's of  course the same reason I still use Windows in a dual boot. XP has never given me any problems to speak of compared to other MS OS's. I think Linux has much better performance, but unfortunately XP is still hanging around to do some things that Linux can't. Seems that recording audio isn't the most practical in Linux for instance (i.e. Jack).

I will say my computers are older (2008 or so) and Dual Cores. Newer computers may work better on Win 7 (or 8). But my old hardware works great with XP and Linux. Also I  have a lot of older software that also works great that wouldn't run on Win 7 or I wouldn't be able to afford to buy the newest version that does run on Win 7. So XP is the best option still at this point.

---

### Post by 1clue on 2014-01-18
The problem with running an operating system past its support date, especially if it's a Microsoft operating system, is that all the virus protection and software updates will start to lapse as well.

You might seriously consider getting your XP into a VM or at least get a good solid backup of it.  Set it up so you can restore the entire C drive and start over any time you want.  All data writing should go to a USB stick or a shared drive.

If you can boot off a read-only partition or in a VM, then you could conceivably continue to use XP way past its end-of-life date.  When you get a virus, just roll back to your "good" snapshot and it's done.

---

