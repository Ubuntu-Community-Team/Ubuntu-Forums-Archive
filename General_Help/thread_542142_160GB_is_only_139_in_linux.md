---
title: "160GB is only 139 in linux?"
date: 2007-09-03
forum: General Help
---

### Post by drywater on 2007-09-03
Hi, I have a 160GB drive. I know it is not "really" 160GBs but it should be more than 139, right?  Gparted sees it as 149GBs.  Formatting it to Ext3, GParted still sees 149 but says 2.52GBs are used.  After mounting it however, File Browsers sees it at only 139.1GBs with the Lost+Found folder.

2 questions.  Why is 2.52GBs used even after a complete reformat? And why does File Browser only see 139GBs when GParted sees 149GB. 

With this much storage it seems silly to worry about the "missing" storage but 20GBs missing = 1/8 of my drive, which seems like quite a bit.

---

### Post by Steveway on 2007-09-03
ext3 takes about 5% of the space for itself.
So that incase you fill the disk up you will still be able to use the operating system.

---

### Post by sumguy231 on 2007-09-03
> I know it is not "really" 160GBs but it should be more than 139, right? 
Right. 160GB (Where 1 GB = 1000MB) = 149GiB(Where 1 GiB = 1024MB). This part is normal. I know formatting a disc with pretty much any filesystem will always lose capacity, but I'm not sure how much loss is normal. I don't know what happened to the other few Gigs though.

---

### Post by megamania on 2007-09-03
> **drywater said:**
> 
With this much storage it seems silly to worry about the "missing" storage but 20GBs missing = 1/8 of my drive, which seems like quite a bit.

[http://ubuntuforums.org/showthread.php?t=78333](http://ubuntuforums.org/showthread.php?t=78333)

it's an old thread where I posted a solution to what appears to be your problem too.

hope that helps.

---

### Post by sloggerkhan on 2007-09-03
My 100gb HD is really 93.16 gb, my 250gb HD is really 232.88gb, so that's about 7% of the drive, and it's because (I am fairly sure) the company rates them w/ mb=1000kb and gb=1000mb or something like that.

In your drive, I'd expect about 148 or 149 actual gb. I'm not sure what to make of, as I don't have the same problem, but it does look like you're missing 10 gigs somewhere.

---

### Post by hardyn on 2007-09-03
maybe a mod would like to sticky this, this question gets asked alot:

a lesson in advertising:
the hard disk industry defines 1GB as 1,000,000,000 bytes.
the computing industry defines 1GB as 1,073,741,824 bytes.
<http://en.wikipedia.org/wiki/Gigabyte>

some arithmetic:
160gb * 1E9 / 1.073471E9 = 149.0 GB

application:
then due to internal fragmentation and journaling of the of the file system,  we lose a little more to the system.

so the 149 GB is correct.

---

### Post by drywater on 2007-09-03
> **megamania said:**
> [http://ubuntuforums.org/showthread.php?t=78333](http://ubuntuforums.org/showthread.php?t=78333)

it's an old thread where I posted a solution to what appears to be your problem too.

hope that helps.

This looks like it will free the reserved space, but what is the reserved space?  Is it the missing 10GBs or the 2.5GBs that are "used" apparently by EXT3?

There is nothing on the drive so I am willing to try whatever I need to and this is not a MUST but would just be nice to have the additional space (and to understand why this is).

> ext3 takes about 5% of the space for itself.
So that incase you fill the disk up you will still be able to use the operating system.

In my case it is just over 5% (about 7% if I'm doing the math right).  Maybe this is normal?

Thanks for your quick responses!

---

### Post by cdrom600 on 2007-09-03
In addition to the aforementioned difference between advertised space and actual space, the ext3 file system takes extra space for its journal file.

---

### Post by megamania on 2007-09-03
> **drywater said:**
> This looks like it will free the reserved space, but what is the reserved space?  Is it the missing 10GBs or the 2.5GBs that are "used" apparently by EXT3?

I'm no expert, but as far as I know it will prevent system instabilities when the hard disk gets full.

However, I zeroed out my reserved space in 2005 and have had no problems so far. But of course, do this at your own risk...  :-|

---

