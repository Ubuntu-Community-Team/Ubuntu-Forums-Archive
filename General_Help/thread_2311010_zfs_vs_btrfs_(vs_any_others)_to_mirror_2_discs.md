---
title: "zfs vs btrfs (vs any others) to mirror 2 discs?"
date: 2016-01-23
forum: General Help
---

### Post by jlparsons on 2016-01-23
I'm setting up a server using low cost/power itx desktop components.  I want to mirror two 1TB discs for storage whilst using a small spare ssd I have lying about for the system and swap partitions.  I have very little experience with mirroring discs, having only used raid previously to RAID0 two small SSDs to reduce load times on a windows gaming pc which, needless to say, was a very different kettle of fish.

Obviously the main goal here is redundancy in case a disk fails, but I gather both zfs and btrfs use stored checksums to verify read data and use mirrored disks to replace failed checksum data with known-good data, repairing the faulty segment and restoring redundancy.  This is very attractive to me!  I have heard that zfs needs ECC ram, though I've also read a very convincing debunking of this which I am inclined to believe.

Anyone have any experience using zfs and btrfs under linux and can suggest a winner?  I'm particularly interested in opinions on the relative effectiveness of their error checking, as well as their ease of use and general stability.

---

### Post by lukeiamyourfather on 2016-01-27
If you don't have ECC memory then don't use ZFS. I'd like to see the "debunking" of this that you read.

---

### Post by jlparsons on 2016-01-27
> **lukeiamyourfather said:**
> If you don't have ECC memory then don't use ZFS. I'd like to see the "debunking" of this that you read.

Sure.  Don't shoot the messenger...

[http://jrs-s.net/2015/02/03/will-zfs-and-non-ecc-ram-kill-your-data/](http://jrs-s.net/2015/02/03/will-zfs-and-non-ecc-ram-kill-your-data/)

TL;DR -
> &#8220;There&#8217;s nothing special about ZFS that requires/encourages the use of ECC RAM more so than any other filesystem.&#8221; Matthew Ahrens, one of the cofounders of ZFS at Sun Microsystems and current ZFS developer at Delphix.

---

### Post by lukeiamyourfather on 2016-01-27
Thanks for the links, that was an interesting read. I'm not worried about the "scrub of death" like described in the article but more about data in the ARC which might be there for very long periods of time (months, years, depending on how often the machine is rebooted). Other file systems don't have the ARC or anything like it. It would seem to me that data in the ARC could have flipped bits that end up in clients hands and then get written back to the pool as seemingly legit data. Maybe ZFS checks data again from the ARC before it goes to the client but that's beyond my technical expertise, maybe someone knows more on that and can share.

The under workings of ZFS aside it just doesn't make any sense to me to go out of the way to setup a file system with integrity at it's core and then not use ECC memory. It's like going motorcycle racing wearing the safest helmet in the world but the rider is otherwise buck naked. If you go with ZFS let us know how it goes in a year or two if you remember this thread at that point.

---

### Post by jlparsons on 2016-01-27
> **lukeiamyourfather said:**
> The under workings of ZFS aside it just doesn't make any sense to me to go out of the way to setup a file system with integrity at it's core and then not use ECC memory. It's like going motorcycle racing wearing the safest helmet in the world but the rider is otherwise buck naked. If you go with ZFS let us know how it goes in a year or two if you remember this thread at that point.

Why wouldn't I use ECC memory?  Because the board/memory I have for the task are not, and because replacing them with server grade stuff would be much more money than I'd be prepared to spend on this setup (my catastrophe backups are offsite, this is for onsite incremental backups).  On the other hand I do have two spare hard drives with enough space that I can have some mirrored redundancy whilst still having plenty of space, and also I can have a filesystem that can spot and repair bit rot for a princely £0.  Two, even!

TL;DR - if I had to ride a motorcycle buck naked and the best helmet in the world was free, I'd wear the helmet.

---

### Post by lukeiamyourfather on 2016-01-28
Good point about it being free. I guess this puts what I was trying to say more eloquently.

> Your chain is only as strong as your weakest link, and if that link is non-ECC RAM, you lose everything ZFS developers have worked so hard to achieve on keeping your data from corruption.

[https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/](https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/)

The rest of the site is worth checking out if you haven't yet. It's a great resource for ZFS on Linux.

---

### Post by jlparsons on 2016-01-30
> **lukeiamyourfather said:**
> Good point about it being free. I guess this puts what I was trying to say more eloquently.

[https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/](https://pthree.org/2013/12/10/zfs-administration-appendix-c-why-you-should-use-ecc-ram/)

The rest of the site is worth checking out if you haven't yet. It's a great resource for ZFS on Linux.

Thanks, will do!

Certainly I agree with the argument that the perfect zfs system designed for data integrity would have ECC ram.  No-brainer.  And I can also understand why devs who put their effort into creating the 'perfect' data-integrity storage system via zfs would find it galling that someone use the fruits of their labour with non-ecc ram.  

What I'm very unsold on is the idea that a non-ECC system with zfs is somehow *worse* from a data integrity point of view than a non-ECC system without zfs, which is what that quote (and lots of other opinions on the intertubes) seems to indicate.  *If* the idea that a stuck bit in ram will wipe out a zfs filesystem is debunked then some element of protection against bitrot via zfs (or indeed btrfs) mirroring is arguably a positive regardless of your ram, surely?

---

