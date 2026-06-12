---
title: "Forum confusion about fakeRAID1 - 7.10 Gutsy Gibbon"
date: 2008-03-04
forum: General Help
---

### Post by markuswells on 2008-03-04
Ok, I have seen a lot of posts lately talking about using dmraid for a fakeRAID 0 setup but other posts say that dmraid is an older solution and that mdadm is generally considered a newer/better setup.

So what is the recommended setup for RAID1 using SATA drives on a MOBO Raid controller (I think thats fakeRAID)?

Also I plan to use the other (my MOBO has 2) on board RAID controller to setup a RAID5 for file storage.

Any feedback on setting up the RAID1 and the RAID5 would be appreciated.

Reference:
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
This tutorial works VERY well but it seems like dmraid has no notification or rebuild capabilities that I am aware of.

[http://ubuntuforums.org/archive/index.php/t-565726.html](http://ubuntuforums.org/archive/index.php/t-565726.html)
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

There is just a lot out there !!
Markus

---

### Post by dcstar on 2008-03-04
> **markuswells said:**
> Ok, I have seen a lot of posts lately talking about using dmraid for a fakeRAID 0 setup but other posts say that dmraid is an older solution and that mdadm is generally considered a newer/better setup.

So what is the recommended setup for RAID1 using SATA drives on a MOBO Raid controller (I think thats fakeRAID)?

Also I plan to use the other (my MOBO has 2) on board RAID controller to setup a RAID5 for file storage.

Any feedback on setting up the RAID1 and the RAID5 would be appreciated.
........

In my experience, hardware based RAID (like what your motherboard does) are transparent to whatever OS that uses the arrays - so Ubuntu will only "see" the virtual disk(s) that the RAID hardware has been set up for.

The only issue with this method is that you may not be able to monitor the RAID setup/operation unless the OS has software specifically for that RAID hardware (this may not be an issue - as long as your RAID array works, then who really cares?.......)

Ubuntu will happily use the disk resources supplied by the RAID hardware as any other disk, it will leave all the RAID work to the hardware (and this is not a bad thing, IMHO).

Most motherboard vendors supply Windows management software for their RAID, but I'm not sure about Linux tools for this job.

You can set up various other software based RAID solutions, but if your hardware has it available then I'd just use it and leave the management at that level, and use Ubuntu like just about everyone else..........    ;-)

---

### Post by markuswells on 2008-03-05
This is not a hardware RAID setup - its a fakeRAID

---

### Post by markuswells on 2008-03-07
anyone have any input?

---

### Post by fjgaude on 2008-03-07
A book could be writtne explaining all the issues regarding raid, software, hardware, fake.

First off, Linux doesn't work well with motherboard raid, period. The only way is through dmraid. Then you have to use whatever utility there is within the BIOS to control how the raid is setup. Such fakeraid is really meant for using of MS Windows. But...

After that then dmraid can be used to mount the assembled array created by the BIOS.

You cannot boot from a raid0; you can from raid1 but many folks wouldn't recommend it.

If you go real-world hardware raid the controller has to have a driver for the version of Linux you are using. There are choices here. They are all expensive if you are looking for good throughput.

Many folks use software raid because now days the CPUs and memory are so fast that software is as fast as hardware, if your drive controller is running off a PCI-e or PCI-X bus. The program many of us use is called mdadm raid. To use it there is steep learning curves. It is extremely flexible, reliable, and easy to setup once you know what you are doing.

---

### Post by markuswells on 2008-03-08
I appreciate the feedback I have gotten so far.

I have tried several different setups to get my RAID1 setup. I have gotten dmraid to work and have installed ubuntu on it and its bootable (woot). RAID1 means I am trying to be prepaired for a drive failure, so I unplug the power from 1 drive and nothing happens (I even write a file to the drive). I understand that dmraid does not throw the error to the OS currently or something like that.

So the question is, after I have rebooted and have found (my bios throws a warning) that a drive has failed, I can replace it. So how do I rebuild that new drive?

This is the drive that has the MBR so a software only RAID is not really an option. Would mdadm provide a better set of tools for notification and rebuild?

---

### Post by fjgaude on 2008-03-08
I would think that you use your BIOS raid software to replace the failed drive. What does the instruction manual for your motherboard say about this?

---

