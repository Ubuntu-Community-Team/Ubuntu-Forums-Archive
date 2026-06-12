---
title: "just got my first ssd"
date: 2017-09-30
forum: General Help
---

### Post by sukelis on 2017-09-30
I just got my first ssd (Samsung 960 EVO M.2 250GB) which I'm using with a Gigabyte H110M-M.2 mobo, 8GB of ram, and a new 2TB hdd.  This is not a gaming rig, but I do some video editing and I'd like to try some virtualization.  

I've done enough searching/reading to become cross-eyed but I do have Lubuntu 16.04.3 desktop installed, using gpt and uefi, no windows, with swap on the hdd.  Hibernate/suspend is working great.  

I have the ssd - /dev/nvme0n1 - partitioned with a 512MiB fat32 /boot/efi partition, a 50GiB ext4 / partition and an extra 50GiB ext4 partition for an additional *nix.  The remainder is currently unallocated.  Before I go any further, I have some questions...

1.  I've read that the ssd's do wear leveling but I don't really understand it.  Also, there were posts that said the ssd doesn't really care about the partitions, ie, that it's functioning at the physical level isn't limited by the partitions.  And I've also read that it's important to leave at least 20% free space.  But what isn't clear is whether it wants all of the space allocated to partitions, and whether that 20% free space is a per-partition value or a whole-device value.  Also, how does unallocated space figure in?  If it doesn't really care about the partitions, then is the unallocated space just as useful for it's wear leveling as free space in the partition(s)?

2.  I've read a confusing number of comments on the necessity of a /boot partition.  I've gone without it, at least in this initial install, which I think means that lubuntu will put the kernel in the / partition.  But does each flavor keep it's own kernels in it's own root?  Or are they all sharing the /boot folder in the first-installed root?  

3.  I've read an equally confusing number of comments regarding the need to tune the ssd... but I noticed that they were older posts.  How much of that still applies to the latest ssd's?  Should fstab still be modified with /noatime?

4.  Some of the older posts also go on about needing to get /var off the ssd, but the newer posts don't really stress this.  Are the newer ssd's not as susceptible to/damaged by the writes?  I mean, you can now get them up to a TB - trying to minimize writes to that much space seems impossible.  I have moved swap to hdd since I use hibernate.  I am leaving /home in the / directory but I plan to symlink/bind the default biggie folders to the large hdd.  So what other directories really need to be moved off the ssd?

I know there's a wealth of information out there, and I've read extensively, but this technology is changing/maturing very rapidly and the information out there... isn't.  So that's why I'm asking for updated answers.

---

### Post by wyliecoyoteuk on 2017-09-30
I personally have a small (16Gb) SLC mode SSD. I use this for Mythbuntu with a 1TB HDD for recording TV and video from security cameras.
I have moved /swap to ram and /var to the HDD.
Modern SSDs do wear levelling, and my only problem was with the / partition filling up with old kernels.
One thing is that file writes happen every time you read a file, but using the noatime switch in /etc/fstab fixes that, or you might want to use relatime or lazytime
A lot of the recommendations online are for older distros and are no longer necessary.

This article is up to date.
[https://wiki.debian.org/SSDOptimization#A.2Fetc.2Ffstab_example](https://wiki.debian.org/SSDOptimization#A.2Fetc.2Ffstab_example)

---

### Post by oldfred on 2017-09-30
I pretty much follow this:
 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 

but also these:

 [http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/](http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/)
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022) 

I use noatime in fstab, you can use with an HDD if desired but I use relatime for HDD.

SSD life is now similar to HDD. 
      
 [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

I also change trim to a daily task with log file. But note that then any data recovery from SSD is reduced as trim has housecleaned all old data. But then you already have a good backup procedure anyway, so data loss is not a concern.

---

### Post by gordintoronto on 2017-10-01
> **wyliecoyoteuk said:**
> ...I have moved /swap to ram and /var to the HDD.


Wylie, you would be better off to just omit the swap. I have 16 GB of RAM, and I've been running for over a year with no swap.

---

