---
title: "Why do we need to make swap partitions?"
date: 2008-06-26
forum: General Help
---

### Post by s3a on 2008-06-26
Why do we need to make swap partitions? Why can't it be like Windows where it uses your installation partition as much as it needs to and if it doesn't need to, it doesn't use at all. Of course Windows doesn't have good memory management and uses alot of pagefiling but my point is why can't Ubuntu have a similar option? Is there any good reason for not having it implemented in that way? Or is it possible to do this?

Thanks!

---

### Post by lisati on 2008-06-26
One reason that *nix has a separate partition for its swap file is that it can be more efficient. Under Windows, the pagefile can be fragmented, which eats into the efficiency.

---

### Post by Rocket2DMn on 2008-06-26
Linux uses the separate partition because it is efficient, can easily be unmounted, and can be shared between linux distributions in a multiboot setup (if you aren't hibernating).  Swap is used to store your RAM during hibernate.

---

### Post by Taxman415a on 2008-06-26
Linux can use just another file on the filesystem for swap just like windows. I'm trying to think off the top of my head the reasons it's not the best approach. One I think is that your swap space is traditionally were core dumps are written out to, so if your filesystem is corrupted, you want your swap on a separate partition. 

I did a little quick research and found this link that a file is a safe option according to Andrew Morton. [http://lkml.org/lkml/2005/7/7/326](http://lkml.org/lkml/2005/7/7/326)
I'm not sure why we still tend towards the swap partition then to be honest. I think it's an old habit from when it was better and safer.

---

### Post by manfer on 2008-06-27
Yes it is something of the past.

Now it seems it is better to use a file for swapping because the efficiency is equivalent than a swap partition and it is easier to resize.

---

### Post by rubicon on 2008-06-27
> **manfer said:**
> Yes it is something of the past.

Now it seems it is better to use a file for swapping because the efficiency is equivalent than a swap partition and it is easier to resize.
It is a matter of taste, actually. Some of Windows admins prefer creating separate primary partition and store swap file with fixed size on it ;) Everything have its cons and pros.

---

### Post by manfer on 2008-06-27
Resizing wouldn't be often needed but imagine a system with 256Mb RAM with a swap partition of 512Mb. If that system is upgraded to 1GB RAM you would probably like to resize swapping to 1Gb at least. With a file for swapping it would be very very easy, but with the swap partition?? In linux systems was suggested to use swap partition because a better efficiency but in this days the efficiency of a swap partition and a swap file are equivalent.

Windows problems with paging file are totally different. No matter you put it on a file or on a different partition, the fragmentation problem is there (is a problem of the NTFS filesystem and as paging is no more than data in that filesystem, the paging inherits the problem too). The only form I knew of improving windows paging a little was putting the paging file in a partition made for it, being that partition the first of a disk. That way paging file can be accessed faster and that is the improvement, though fragmentation would be still present, no way to correct that.

---

### Post by rubicon on 2008-06-27
> **manfer said:**
> Resizing wouldn't be often needed but imagine a system with 256Mb RAM with a swap partition of 512Mb. If that system is upgraded to 1GB RAM you would probably like to resize swapping to 1Gb at least. With a file for swapping it would be very very easy, but with the swap partition??Yep, that makes sense. Though *nix systems were (and still are *sigh*) generally server OSes, and servers generally not getting upgraded often enough.

> **manfer said:**
> in this days the efficiency of a swap partition and a swap file are equivalent.Citation needed ;)

> **manfer said:**
> No matter you put it on a file or on a different partition, the fragmentation problem is there (is a problem of the NTFS filesystem and as paging is no more than data in that filesystem, the paging inherits the problem too).Not agreed, elaborate please. From my point of view, single file with fixed size could be allocated in one shot, and fortunately without any fragmentation. Therefore, any data written into it won't be affected by fragmentation unless ntfs driver decide to do something nasty.

> **manfer said:**
> The only form I knew of improving windows paging a little was putting the paging file in a partition made for it, being that partition the first of a disk.Agreed, this improves performance more or less.

---

### Post by Canis familiaris on 2008-06-27
Option to use SWAP file must be given during install.

---

### Post by manfer on 2008-06-27
@rubicon: The citation is on the 4th post by Taxman415a. I didn't read to much about it but can be found in that citation and on ubuntu wikis too. It is something since kernel 2.6, don't know exactly why.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

which would point you to:

[http://en.wikipedia.org/wiki/Paging#Swapping_in_Linux](http://en.wikipedia.org/wiki/Paging#Swapping_in_Linux)
[http://lkml.org/lkml/2005/7/7/326](http://lkml.org/lkml/2005/7/7/326)

About the paging file in Windows. Yes sorry, fragmentation occurs when paging file automatic resizing is enable, not with single file with fixed size. Thanks for the correction.

---

### Post by rubicon on 2008-06-27
> **Anurag_panda said:**
> Option to use SWAP file must be given during install.
Absolutely yes.

There are some ideas brainstormed:
[http://brainstorm.ubuntu.com/idea/8092/](http://brainstorm.ubuntu.com/idea/8092/)
[http://brainstorm.ubuntu.com/idea/2436/](http://brainstorm.ubuntu.com/idea/2436/)

**@manfer**: Thanks for the links, very interesting. Swap files are really declared to be as efficient as separate partitions, so it is time for Ubiquity or debian-installer to include an option to swap on file as an alternative to partition.

---

### Post by justleen on 2008-06-27
* swap is not absolutly neccesary (I run a thinclient machine as LAMP server w/o swap)
* during install you can actually skip creating swap.. you wil just get a warning
* "resizing" swap paritions shouldt be a problem, you can always add more swap paritions if need be, the OS will use it as one big swap
*performance wise there is no good reason to have a swap file vs. parition
* you could have a virtual disk as swap == swap file..

---

