---
title: "Newbie needs help setting up Ubuntu with RAID 5"
date: 2008-01-10
forum: General Help
---

### Post by Guy Gizmo on 2008-01-10
I'm responsible for setting up a new file server so that it runs Ubuntu with RAID 5.  My post title wasn't entirely true - I'm not really new to Linux or unix environments.  If there wasn't a RAID 5 at all, I'd be confident in installing Ubuntu, getting it up and running, and configuring Samba.  I'm comfortable working with the command line, though I don't know that many linux/unix commands off the top of my head.  But I'm a little unsure of myself when it comes to configuring and maintaining a RAID 5 array on this new server, because I've never done anything like that before.

In case it comes up, and so I don't have to post this server's specs, I'll link to its product page [here]("http://www.globalcomputer.com/applications/SearchTools/item-details.asp?EdpNo=2792628&CatId=2672").
So the questions I have are:

1. How do I actually set up RAID 5?  Is it part of the Ubuntu installer, or do I do it separately?  And is this a software or hardware RAID?

2. Which version of Ubuntu do I want?  I think I want the 'alternate' desktop install disc, but I'm not sure.

3. How should I partition everything once the RAID is set up?  Should the Ubuntu installation be on a separate partition?  Where does the swap partition go?

I've googled around for information about this, but after reading through several pages and a tutorial or two I'm still not sure what exactly I'm doing.  I'm one of those people that always prefers working in a nice, intuitive GUI over the command line, so whenever I have to use the command line I'm never quite sure where to start or how to figure out what I'm supposed to do.  (Like I said, I'm comfortable working in the command line, but I just don't know that many commands.)

So if anyone is willing to hold my hand a bit here, I'd be very appreciative!  I'm very interested in learning to use Ubuntu and linux in general, but I learn best by example and demonstration over reading documents and man pages. :)

---

### Post by Crakie on 2008-01-10
I´ll try to get you going :) I set up a couple of RAID arrays myself, but never in a professional environment.

> 1. How do I actually set up RAID 5?  Is it part of the Ubuntu installer, or do I do it separately?  And is this a software or hardware RAID?

The question is: do you *want* software or hardware Raid? If hardware, then it's just a matter of choosing a supported RAID controller. There is not much to set up: Ubuntu will 'see' only a single drive, because the controller does all the thinking. Please note that most modern motherboards are equipped with some sort of RAID controller, but these usually cannot compare to the ones you buy separetely. If you want hardware RAID, you probably need to go shopping.

The performance of software raid is fine, by the way. See next question on how to set it up.

> 2. Which version of Ubuntu do I want?  I think I want the 'alternate' desktop install disc, but I'm not sure.

Last time I checked, you do indeed need the alternate install disc, because the LiveCD does not support RAID. It should not be a difficult to set it up though. When choosing a drive and a partition scheme, you will be able to assign them to a RAID array of your choosing.

Personally, I had to do it the hard way. Ubuntu (and Linux in general) has some problems with recognizing my controllers. I had to partition and create RAID arrays myself using an Arch Linux CD (but I guess any distro would do as long as it supports RAID). The commands you need to look into are 'cfdisk' for partitioning, 'mdadm' for setting up RAID and then a utility to create a file system (like 'mkreiserfs'). I wouldn't worry about all this unless the alternate installer fails.

> 3. How should I partition everything once the RAID is set up?  Should the Ubuntu installation be on a separate partition?  Where does the swap partition go?

In software RAID, you need to partition *before* creating a raid. Let's say you have 3 drives. You could create a single partition on everyone and then assign them to a RAID 5 arrays. But you could also create 2 partitions on each drive and assign them such that you create 2 RAID arrays. It not necessary, but still wise, to assign partitions of equal size to a RAID array.

As for what scheme is best, well... that's a hard question, as there are so many options, each with advantages and disadvantages. Just a suggestion:

1) A separate partition of 10 - 20 Gb for the OS (you could make it a RAID array)
2) A separate RAID5 array for file storage (using almost all of the remaining space).
3) A small partition for the swap file.

Hope this helps.

---

### Post by Guy Gizmo on 2008-01-10
Thanks for your help so far.

I've hit my first major snag - I can't figure out how to set up the RAID in the Ubuntu installer!  Software RAID is definitely what I want, but there doesn't seem to be any option to configure that.

When I get to the part where I can partition the disks, I tried making a partition that filled each disk and assigning it to be 'physical raid volume'.  The installer then complains I haven't created a mount point!  I tried partitioning each disk identically, but then it complains that there are multiple partitions with the same mount point.  I then tried partitioning each disk identically, except making all the partitions on disks 2-4 all be 'physical raid volumes', but there's no option to set up the RAID!

I'm already lost at this point!  Is there some option in the installer I'm missing?

---

### Post by Guy Gizmo on 2008-01-10
Update: I've made progress!  There was an option in the partitioner that I probably missed just because I miss obvious things like this for setting up a RAID volume.  I'm still figuring out exactly how to set up the kind of partitioning scheme I want.  (I'd like three partitions across the RAID 5 - one for the OS, one for files, and one for swap.)

ALSO, I just realized that the server's BIOS has an  option for setting up a RAID.  Does this mean the server has a hardware RAID controller?  Even though all 4 hard drives were configured to be RAID 5, the Ubuntu installer still saw 4 unformated hard drives, so I'm not sure what's going on with that.

---

### Post by fjgaude on 2008-01-10
I don't know much but there is one thing I do know: you can't boot from a software raid5. Think about it, each  drive of the array has something a little different and the kernel needs to be loaded before the array can be assembled.

I would consider using one disk for the OS, and the others for a software raid5 array using mdadm to create the array after you have the OS installed and it working as you like it. That's what I do.

That's my thought for now. (Hi, Crakie!)

---

### Post by Guy Gizmo on 2008-01-10
Well, here's what I did.  I configured each 500 GB hard drive identically, to have the following partitions:

5 GB raid volume
500 MB raid volume
494.5 GB raid volume

I then used the software RAID configuration tool in the Ubuntu installer to create three RAID 5 volumes across all four hard drives, and formatted them thusly:

15 GB ext3 (for OS)
1.5 GB swap
1.5 TB ext3 (for files)

The installer gave me a warning message after setting this up that the installer couldn't see any changes to the hard drives until AFTER I rebooted, and I don't know why.

Furthermore, apparently I can't boot form a software RAID 5, so this setup is probably no good.

I guess I want a hardware RAID 5 then.  I'm pretty sure this server has a hardware RAID controller, because I can set that up in the BIOS.  But the Ubuntu installer still sees 4 separate hard drives regardless!

Does anyone know what I'm doing wrong?  Do I have to somehow manually set up the RAID controller in the Ubuntu install or something?

---

### Post by fjgaude on 2008-01-10
The raid controller that is on motherboards are really software raid, or as some call it: fakeraid. If you have a true hardware controller in your server make sure you have the driver for Ubuntu Linux, else it will not work.

You can boot from a true hardware raid if you have the driver that goes with the board that works with Linux. Dell, Areca, Adaptec, Highpoint have, Promise doesn't, I know. But that's about the limit of my knowledge.

---

### Post by Guy Gizmo on 2008-01-10
It almost certainly is fakeraid, because the server specs don't include any mention of a hardware RAID controller.  Furthermore, what the BIOS says about the RAID configuration of the hard drives has absolutely no bearing on what the Ubuntu installer sees.

Basically, what I want to do is have the OS, swap, and files for this server to be in the RAID so that if one of the hard drives die, the server will still boot and run.  I don't particularly care how I go about accomplishing this.  Linux software RAID sounds like the best and easiest option, except I can't boot to any partitions in the RAID.  I could install the OS on a seperate, non-RAIDed partition, but then if that hard drive fails the server won't boot.

Any ideas about how I'm supposed to do this?

---

### Post by Guy Gizmo on 2008-01-10
Another update: a Linux savvy friend of mine has suggested a good idea, which is to ignore the fake hardware RAID, and to create a seperate software RAID-1 partition that mounts to /boot.  So what I'm doing now is partitioning all the drives to have a 1 GB partition at their start, and all the rest of the free space in a second partition.  So the setup is:

1 GB ext3 RAID-1 partition between sda1 and sdb1, mounted at /boot
1 GB swap RAID-1 partition between sdc1 and sdd1
1.5 TB ext3 RAID-5 partition  between sda2, sdb2, sdc2, and sdd2.

So it can still boot from sda1, and if sda should fail, it can boot from sdb1.  Hopefullly it'll go well!

---

### Post by fjgaude on 2008-01-10
Okay, but be sure to figure out if one of the raid1 drives fail that you can still re-boot. <sigh>

---

### Post by Crakie on 2008-01-11
> **Guy Gizmo said:**
> Another update: a Linux savvy friend of mine has suggested a good idea, which is to ignore the fake hardware RAID, and to create a seperate software RAID-1 partition that mounts to /boot.  So what I'm doing now is partitioning all the drives to have a 1 GB partition at their start, and all the rest of the free space in a second partition.  So the setup is:

1 GB ext3 RAID-1 partition between sda1 and sdb1, mounted at /boot
1 GB swap RAID-1 partition between sdc1 and sdd1
1.5 TB ext3 RAID-5 partition  between sda2, sdb2, sdc2, and sdd2.

So it can still boot from sda1, and if sda should fail, it can boot from sdb1.  Hopefullly it'll go well!

That seems an excellent way to get things running. I completely forgot to mention the requirement of a seperate /boot but you seem to have things under control now (hi fj ;))

---

### Post by tad1073 on 2008-01-12
I need help setting up ubuntu on a RAID Array. Info [Here](http://ubuntuforums.org/showthread.php?t=657796), [Here](http://ubuntuforums.org/showthread.php?t=664316) and [Here](http://ubuntuforums.org/showthread.php?t=630644&page=2)

---

### Post by fjgaude on 2008-01-13
> **tad1073 said:**
> I need help setting up ubuntu on a RAID Array. Info [Here](http://ubuntuforums.org/showthread.php?t=657796), [Here](http://ubuntuforums.org/showthread.php?t=664316) and [Here](http://ubuntuforums.org/showthread.php?t=630644&page=2)

Read, study this link and you will know what to do:

[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

It was entered in 2003 but is still accurate and valid.

Let us know how you handle your array.

---

