---
title: "Adding a new disk, want to use RAID 0"
date: 2007-06-13
forum: General Help
---

### Post by RTrev on 2007-06-13
I've been using Ubuntu for a while now, but when I install I always choose the "easy" option of telling Ubuntu to use all of the disk and do whatever it wants with it.  Hence, my knowledge of partitioning is lagging.

I've been running on a single Western Digital 74G Raptor, and today I'm having a second one delivered which I want to set up as RAID 0 for a (hopefully) super-fast system disk.  Later I will add a couple more disks, probably in RAID 1, for my data.

I've got the "fake raid" on my motherboard, but am planning to just ignore it after all I've read so far.  Seems like Linux Software Raid is a better solution in this case?

I'm running Feisty-64, and the machine, if it matters, is home-made with a Machspeed MSNV-939 mobo and an AMD X2 3800+ CPU with 4G of RAM installed.

So, I wonder if some kind soul could give me a pointer about the best way to do this when the new disk arrives later?

As an aside, I thought maybe I could get a head start on the project by installing mdadm from the repository, and was dismayed to find that it didn't just install.. it actually came right up and ran.. asking me questions about partitions and wanting to *do* something.  I wasn't ready!  I just wanted to get it installed so I could browse the man page for it.  I haven't rebooted since.. hope I didn't hose the system already.  :D  I said "none" when it asked about partitions, and "no" when it asked something about enabling the stuff now.  It then did some lengthy dance involving terms like "emergency" and "intrafms" and whatever.

I have nothing on the system that I care about, and if a complete reinstall from scratch is the easiest method, that isn't a problem.

So, how do I splice a second, identical, WD 74G Raptor into my system for a RAID 0 system disk?

Please don't use any words of more than one syllable.  ;)

Thanks!
Bob

---

### Post by ikonia on 2007-06-13
1.) really consider if you want to use raid 0 - it won't add any performace to the naked eye everone who owns a raptor seems to think it does. If you lose or corrupt one disk - your whole box is gone.

I wrote a guide in reference to this post. You should follow the same process for raid0 as raid1 basically. 

Remember not to put /boot on raid0 

[http://ubuntuforums.org/showthread.php?t=454116](http://ubuntuforums.org/showthread.php?t=454116)

---

### Post by RTrev on 2007-06-13
> **ikonia said:**
> 1.) really consider if you want to use raid 0 - it won't add any performace to the naked eye everone who owns a raptor seems to think it does. If you lose or corrupt one disk - your whole box is gone.

I wrote a guide in reference to this post. You should follow the same process for raid0 as raid1 basically. 

Remember not to put /boot on raid0 

[http://ubuntuforums.org/showthread.php?t=454116](http://ubuntuforums.org/showthread.php?t=454116)

Thanks for  the quick reply, and I'm off to read your guide now.  But RAID 0 won't add perceptible speed improvements?  I know it's less robust, but I figure the worst that will happen is I have to reinstall the OS.. my data will be elsewhere.

How can RAID 0 *not* improve performance?  I mean, what is the common fallacy about this that I've apparently succumbed to? 

Thanks again!
Bob

---

### Post by bigken on 2007-06-13
raid 0 stay away from it no parity if it gets corrupted youve had it 

I have recovered files from raid 0 on a windows system but never on linux 
and it was a bloody nightmare of a job

---

### Post by ikonia on 2007-06-13
it won't give you any performance increase because your pretty much using low end home PC components.

Its only really noticable on massivly high IO systems with high read and write times and a good disk controller.

As the above poster said, for the majority of home users - just stay away.

---

### Post by RTrev on 2007-06-13
> **bigken said:**
> raid 0 stay away from it no parity if it gets corrupted youve had it 

I have recovered files from raid 0 on a windows system but never on linux 
and it was a bloody nightmare of a job

Okay, but I can't, off-hand, see any point to using RAID on a system disk unless it was a production environment where downtime was a big no-no.  If my system disk fails, I rma it, get a new one, and reinstall.  If I'm going to have an extra and fast, but tiny, disk, I would rather use it for something that would make my day-to-day experience better.  Heck, I'm a newbie.. I reinstall all the time anyway.  ;)

I'll be buying some big disks for data, and those I want to use at least RAID 1 on if possible, but for the system disk I just want speed and damn the torpedos.  :D

What would you do with a second Raptor 74G if you had one?

Thanks,
Bob

---

### Post by bigken on 2007-06-13
Have you though about raid 5

---

### Post by ikonia on 2007-06-13
> 
If I'm going to have an extra and fast, but tiny, disk, I would rather use it for something that would make my day-to-day experience better.


you won't see a difference, and it won't make your day to day experience better, and can provide an extra overhead of admining, eg: all file systems will be on a meta device rather than a solid disk so things like kernel updates have more potential of not finding the right disk at updates.

Your also more likley to have corruption more so on home kit so you'll spend more time fixing and re-building than having a usable system. Its not just if a disk fails but every time there is a problem with your file system full stop. 

I do have 2 Raptors in my desktop machine. I use them seperatly as single fast disks and it works fine. I won't raid them as I won't see any benifit and just create myself an admin overhead.

---

### Post by RTrev on 2007-06-13
> **bigken said:**
> Have you though about raid 5

I've only got two disks, well, when the second is delivered later I'll have two disks.  Doesn't RAID 5 require a minimum of three disks?

Not sure what you're getting at here?  Do you mean later, say get two big disks, and then use the Raptor somehow with those?

---

### Post by RTrev on 2007-06-13
> **ikonia said:**
> you won't see a difference, and it won't make your day to day experience better, and can provide an extra overhead of admining, eg: all file systems will be on a meta device rather than a solid disk so things like kernel updates have more potential of not finding the right disk at updates.

Your also more likley to have corruption more so on home kit so you'll spend more time fixing and re-building than having a usable system. Its not just if a disk fails but every time there is a problem with your file system full stop. 

I do have 2 Raptors in my desktop machine. I use them seperatly as single fast disks and it works fine. I won't raid them as I won't see any benifit and just create myself an admin overhead.

So you just use one as your system disk,  and the other as a data disk?  

I suppose I could put current projects on the 2nd Raptor while working on them, and then move them off to the bigger and slower storage disks later.  Or maybe I should just give the 2nd Raptor to my wife, and use just the one.  Hmm.  Looks like I leapt into a purchase too  fast!  :(

---

### Post by ikonia on 2007-06-13
with respect, "big slow disks" - and "fast raptors" you won't really notice to the naked eye unless your doing something VERY disk intensive like video editing (which I don't know if you are).

for projects like office work, software development, listening to music etc etc etc you won't see the difference in a 36 gig raptor and a 500 gig standard sata disk - you just won't see it to the naked eye.

---

### Post by RTrev on 2007-06-13
> **ikonia said:**
> with respect, "big slow disks" - and "fast raptors" you won't really notice to the naked eye unless your doing something VERY disk intensive like video editing (which I don't know if you are).

for projects like office work, software development, listening to music etc etc etc you won't see the difference in a 36 gig raptor and a 500 gig standard sata disk - you just won't see it to the naked eye.

Darn it, I wish I'd asked *before* I ordered the second Raptor!  Video editing sounds like fun.. maybe I should take it up to justify this disk.  ;)

I was planning on getting a couple of WD Caviar SE16's for my data, which would be kind of overkill but I could put all of our music and videos and whatnot on there and not have to worry about space too much.

My wife has a single 250G WD drive.. perhaps the best thing would be to set her up with the extra Raptor as her system/boot disk?  Even if it wasn't noticeably faster, at least she'd have her data and her OS kept apart, so an OS re-install wouldn't be such a hassle.

Thanks.. I really appreciate your help!!

Best,
Bob

---

### Post by bigken on 2007-06-13
have you cosidered an external ethernet hard disc enclosure to store your data ect then everyone on the network can share there media

asuming you have a router

---

### Post by RTrev on 2007-06-13
> **bigken said:**
> have you cosidered an external ethernet hard disc enclosure to store your data ect then everyone on the network can share there media

asuming you have a router

Someone else suggested this to me a while back.. I think he called it NAS - Network Attached Storage?  I'm not clear how that would be any more workable than just sharing the data off my own machine?  Our only router is just the DSL modem.. Westell WireSpeed Dual Connect.

I'm certainly open to the idea.. will have to research it a bit.

Thanks,
Bob

---

### Post by bigken on 2007-06-13
why I think its a good idea is even a pc in your house breaks down all your files are still on the network via the NAS device to access form othe pc's for an adsl modem router look at the neatgear realy easy to setup and very reliable ;)

---

### Post by arbulus on 2007-06-13
> **RTrev said:**
> Someone else suggested this to me a while back.. I think he called it NAS - Network Attached Storage?  I'm not clear how that would be any more workable than just sharing the data off my own machine?  Our only router is just the DSL modem.. Westell WireSpeed Dual Connect.

I'm certainly open to the idea.. will have to research it a bit.

Thanks,
Bob


Having a router is a very good idea.  Even if you don't use a your disk in a NAS, it's still good to have a router because they contain firewalls and NAT, which is very important for your computer's safety.


Another thought on the multiple hard dive setup:
Instead of using a RAID, perhaps you could set up root, /boot and swap partitions on the first hard drive and /home partition on the second hard drive.  That way, both drives are being utilized.

---

### Post by RTrev on 2007-06-13
> **arbulus said:**
> Having a router is a very good idea.  Even if you don't use a your disk in a NAS, it's still good to have a router because they contain firewalls and NAT, which is very important for your computer's safety.

I was under the impression that we had a NAT router in the form of our Westell DSL modem.. we don't?  

> Another thought on the multiple hard dive setup:
Instead of using a RAID, perhaps you could set up root, /boot and swap partitions on the first hard drive and /home partition on the second hard drive.  That way, both drives are being utilized.

Hmm... that sounds promising.  Probably a good use of the extra 74G.  Being a real newbie still, and having  allowed the install routines to do whatever they wanted, I'm not totally clear on the conventions used for the various partitions.  Is there a good explanation of this somewhere that somebody could give a link to?

Thanks much, all of you!!
Bob

---

### Post by arbulus on 2007-06-13
> **RTrev said:**
> I was under the impression that we had a NAT router in the form of our Westell DSL modem.. we don't?  

Hmm... that sounds promising.  Probably a good use of the extra 74G.  Being a real newbie still, and having  allowed the install routines to do whatever they wanted, I'm not totally clear on the conventions used for the various partitions.  Is there a good explanation of this somewhere that somebody could give a link to?

Thanks much, all of you!!
Bob


About the modem:  So it must be a combo Router+Modem thing?   Sorry about that.  I guess I misunderstood.  


Partitioning can be a bear to get your head around.  I'll try to find some good how to and explanation links for you and update my post as soon as I can.

---

### Post by RTrev on 2007-06-13
> **arbulus said:**
> About the modem:  So it must be a combo Router+Modem thing?   Sorry about that.  I guess I misunderstood.  

Yeah, with a Firewall built in too, although it seems like a NAT router is probably all the firewall one would need.

> Partitioning can be a bear to get your head around.  I'll try to find some good how to and explanation links for you and update my post as soon as I can.

Appreciate it.. thanks!

---

### Post by arbulus on 2007-06-13
Here's a couple of links that have some pretty good info.

[https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html)

[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html)

I hope this helps.

---

### Post by RTrev on 2007-06-13
> **arbulus said:**
> Here's a couple of links that have some pretty good info.

[https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/7.04/installation-guide/i386/partitioning.html)

[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html)

I hope this helps.

Found and bookmarked.  Will be reading it beginning immediately!  Thanks for all the help!!!

---

