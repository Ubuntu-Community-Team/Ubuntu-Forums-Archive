---
title: "RAID unmount failed during shutdown"
date: 2007-08-04
forum: General Help
---

### Post by Ryoojin83 on 2007-08-04
I looked around and couldn't find any reasonable answers.

I recently installed Ubuntu Server (Feisty Fawn) on my machine, and when I shutdown the system, two of the three raid arrays fail to unmount.   Is there a way to fix this?   When I was searching,  someone was having the same problem, and someone told him to just ignore it if he wasn't loosing data.  Well, I haven't lost any data YET, but I really don't want to risk it.   

Any ideas on what might be going wrong?  Just used the install disk to create the arrays.  mdadm is being used. 

Thanks for your time.


EDIT:   I am attempting a 'dpkg-reconfigure mdadm' to see if that helps.    I am going to let the array rebuild itself before I do a reboot test.

---

### Post by fjgaude on 2007-08-04
Gosh, I use mdadm raid on a raid5 array and don't seem to have the problem... no data loss ever.

How do you test to make sure two drives didn't unmount? Using another partition? Another computer? Live CD? <smile>

frank

---

### Post by Ryoojin83 on 2007-08-04
They Fail during shutdown

---

### Post by Midahed on 2007-08-04
I'm running with raid1 on 7.04 Feisty 64-bit workstation and have seen the same problem, but only once.  No idea what caused it, though.  I decided to just keep an eye on it to see if it happens again (it hasn't so far).

Mike

---

### Post by Ryoojin83 on 2007-08-04
I get it every time.  32-bit feisty

I also get this message on boot

"""
mdadm: No devices listed in conf file were found.
"""

my raid 0 swap will not activate on boot either --> "Unable to find swap-space signature"

---

### Post by Midahed on 2007-08-04
Has it always done this since you built it, or is this something new?  Which partitions are raided and which (if any) are not?  What flavour of raid do you have 0?, 1?, 5?

Mike

---

### Post by Ryoojin83 on 2007-08-04
I used to run 6.10 and I never seemed to have this problem. 

I recently did a complete rebuild of my machine (all hardware is the same though)

I am running raid 1 (root fs, md0), raid 0 (swap, md1), and raid 5 (archive area, md2)  

Only md0 and md1 are failing at reboot (or shutdown)

I also no longer get the mdadm error

[http://hodza.net/2007/07/25/no-devices-listed-in-conf-file-were-found-ubuntu-704/](http://hodza.net/2007/07/25/no-devices-listed-in-conf-file-were-found-ubuntu-704/)

followed that and added the sleep 10 to the init file.

---

### Post by Midahed on 2007-08-04
Also,  can you paste a copy of the content of  /etc/mdadm/mdadm.conf

Finally, what do you get if you do cat /proc/mdstat

Mike

---

### Post by Midahed on 2007-08-04
So, your root filesystem is raid1 (mirrored) on md0.  Do you have a separate non-raided boot partition or not?  

Your swap partition is raid 0 (striped) on md1 - is that right?  I wouldn't claim to be an expert, but isn't that a bit odd or is that raid 0 a typo?

Mike

---

### Post by Ryoojin83 on 2007-08-04
I have to hand write all these since the machine is not networked for now

/etc/mdadm/mdadm.conf

DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=[the uuid]
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=[the uuid]
ARRAY /dev/md2 level=raid5 num-devices=2 UUID=[the uuid]


/proc/mdstat

Personalities : raid[0] raid[1] raid[6] raid[5] raid[4]
md2: active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
       879100608 blocks level 5, 64k chunk, algorythm 2 [4/4] [UUUU]
md1: active raid0 sde2[0] sdf2[1]
       3935744 blocks 64k chunk
md2: active raid1 sde1[0] sdf1[1]
       37110016 blocks [2/2] [UU]

---

### Post by Ryoojin83 on 2007-08-04
I'll admit I'm kinda new to raid.

I do not have an un-raided boot partition, it has always seemed to work without it.

yes, my root FS is md0 with raid 1, and my swap is md1 with raid 0

---

### Post by Midahed on 2007-08-04
I'm not familiar with that particular workaround - is the 'sleep' fix to get over the bug that causes a race condition that means the system tries to access the raid devices before mdadm has got its act together:-

[https://bugs.launchpad.net/ubuntu/+s...ols/+bug/79204](https://bugs.launchpad.net/ubuntu/+s...ols/+bug/79204)
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/103177](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/103177)

If so, my understanding is that's something that affects boot-up, not shutdown.  But either way, you're still seeing the 'mdadm: no devices listed' error....

I'm lost for ideas.  Perhaps it would be worth putting quiet=n in your /boot/grub/manu.lst file (I'm assuming you use grub) so that the boot process is verbose and you can see if there's anything else that it's complaining about?

Mike

---

### Post by Midahed on 2007-08-04
> **Ryoojin83 said:**
> ....my raid 0 swap will not activate on boot either --> "Unable to find swap-space signature"
Does the system ever see this device as swap space?  Did you do a mkswap /dev/md1 at some point?  Having asked that, I now remember that you did a clean install, so presumably that _should_ have created swap correctly - bit it might be worth checking that md1 is configured for swapping.  I'd use the free command and look at the total, used and free space for swap.  I forgot to do mkswap on my system and all three entries were zero.

Ideally, of course, a system should rarely swap (assuming it has a decent amount of memory), which is why I thought it was strange to have a striped raid for swap.

Mike

---

### Post by Ryoojin83 on 2007-08-04
After I put in the 'sleep 10' into the init file, I no longer see the mdadm warning at boot time.


I am going to try and reinstall 6.10 server and see what happens ill let you know later tonight

---

### Post by fjgaude on 2007-08-04
> **Ryoojin83 said:**
> 
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=[the uuid]
A[UU]

I must say there are many schools of thought about using raid for boot partitions, but using raid0 for swap is really off the wall.

It's easy to rebuild, reinstall the OS if a disk fails, but data is something else, and that's why raid5 is so good, important.

Is it possible as the Linux kernels have been updating to handle raid better the latest ones don't like raid0 for swap?

Just something to think about.

frank

---

### Post by Ryoojin83 on 2007-08-04
I guess I don't really see what is off the wall about using RAID 0 for swap.  
I have 2 partitions on each drive, the root partition (38GB) and swap partition (2GB), and the drives have to have identical root partitions in order to mirror.  so what do I do with the remaining 2 partitions?  I just wanted to make one big swap, with "better performance",  though I doubt it would since its pulling off of drives with another raided partition.   I guess I could just have made 2 swap spaces.  Didn't cross my mind at the time to make more than one though.

what do you recommend?  2 separate swap spaces?

---

### Post by fjgaude on 2007-08-04
I guess I would be thinking that the swap should be raid1. Like others have said I'm no expert... I just do what others have advised over the years and use logic to make sure I'm getting the speed and safety, reliability needed for the task at hand.

Raid is complicated and when things go wrong it's not easy to track down what is going wrong. So, raid5 for data, no raid to boot. There are experts around and I think this is what they would suggest, from years of experience running big servers.

Linux software raid is coming into its own as the kernel is getting updated every few months to handle it safely. What with fast memory and CPUs, it is hard to not use software raid. The SCSI folks are still into hardware raid, but boy is it expensive compared to SATA.

On the other hand, we each have to do what we feel is right for us, and our pocket books, eh?

frank

---

### Post by Ryoojin83 on 2007-08-04
This is such a nightmare... I reinstalled using 6.10, which used to work perfectly....  now my machine just boots into busy box...  *tear*  what happened to ubuntu..

boots into busy box with 6.06.1 too

---

### Post by fjgaude on 2007-08-04
It's not your your boot raid1 array. I don't know how to suggest you go about installing Ubuntu on a raid pair except through the live CD in character mode, and even that might take the DVD version, or the server version.

Good luck... and keep us posted on your progress. <smile>

frank

---

### Post by Ryoojin83 on 2007-08-05
I am using the server install disk.

Just reinstalled using only the system drives (all other drives removed) and I also just setup 2 swap partitions (no more raid 0) and just a raid one on the root fs.  Still no luck.  Still getting the "no devices listed in conf file were found" message, unless I add the sleep 10 to the init file.  And the raid still fails on shutdown...  I'm so lost.. this was never a problem before.  I have tested with 6.06.1 server, 6.10 server, and 7.04 server.   *tear*  I really want to get this working.

Anyone else have any ideas?   They would be greatly appreciated.

---

### Post by Midahed on 2007-08-05
I'm glad you've dumped the raid0 swap. 

I'm running 7.04 Feisty on a raid1 configuration.  I just have root and swap partitions and both are configured as raid1.  I'd read that a non-raided swap can cause the system to stop if a drive fails, whereas a raid1 swap will keep going.  Of course, there is the processor overhead as a price to pay for raided swap, but if things are working as they should and the system is rarely swapping, that overhead is small.  I don't have a separate boot partition, so I'm booting off my raid1 root filesystem.  I built my raid based on my original system disk containing live data - full story here - [http://ubuntuforums.org/showthread.php?t=504463](http://ubuntuforums.org/showthread.php?t=504463).  I didn't do a re-install, so unfortunately I have no experience of setting up a raid from scratch using the installation CD.

Let me make sure I have understood the last few steps you have taken...

You removed your raid5 drives from the system (to protect the data presumably) and rebuilt from the installation CD.  Which version of the CD did you use this time round - in an earlier post you said you have tried several separate versions of Ubuntu?  You now have a clean installation  with a raid1 root filesystem and non-raided swap.

I'm not surprised you had to put the 'sleep' fix back after the re-install.

However, you're still seeing the raid fail on shutdown.  That's really weird.  The only thing I can suggest is that you post a full step-by-step description of the process you used to complete the new installation in the hope that someone who's more familiar with that approach will spot what's gone wrong.  The fact that the system apparently wasn't recognising the swap device implies that something is going wrong during installation.

Maybe there's a really odd hardware fault creeping into your system?  It would have to be one in the 'completely wild' category, but I've seen plenty of similarly extreme things happen in the past.  I'd also set things up so you can see the boot and shutdown process in 'verbose' mode to see if you can spot anything else that might be giving rise to the problem.

**[EDIT]**  Having re-read the whole thread I'm more inclined to think you might have a hardware problem - especially as a re-build of your original 6.10 ends up in busybox.  If you've had your hands in the case isolating drive cables, etc, it might be worth checking that all the cables are seated OK and nothing else has been disturbed.

**[Another edit]**  I'd also be inclined to take a look at you BIOS settings to make sure something odd hasn't happened there as well.  Are you generally running everything at defaults or is it tweaked for over-clocking, etc...?

Mike

---

### Post by Ryoojin83 on 2007-08-05
Another weird thing that bothers me, is that 7.04 sees my IDE HDDs as Serial drives, Labels them sda, sdb, instead of the old hda, hdb

Testing my HDDs now..

---

### Post by Midahed on 2007-08-05
> **Ryoojin83 said:**
> Another weird thing that bothers me, is that 7.04 sees my IDE HDDs as Serial drives, Labels them sda, sdb, instead of the old hda, hdb
I think that's normal behaviour.  I recall reading that, for systems that support PATA and SATA drives, it just depends on the kernel and what modules happen to be loaded first in your initrd.

I'm pretty sure that's the case, but it may be worth your while Googling for confirmation.

Mike

---

### Post by Ryoojin83 on 2007-08-05
Well, I just installed again for the...15th time...and now it just works...  This is the weirdest thing ever... I reinstalled using 6.10.   Not doing it again... :-)


Despite my hardship.. I still love ubuntu!  haha

(now I just have to install my raid 5 array)  *prays*

---

### Post by Midahed on 2007-08-05
> **Ryoojin83 said:**
> Well, I just installed again for the...15th time...and now it just works...  This is the weirdest thing ever... I reinstalled using 6.10.   Not doing it again... :-)
It's not really that weird, is it?  Your 6.10 installation originally gave you no problems - it was only the latter re-installation that failed because it dropped you into busybox.

I would expect 6.10 to be fine, because it used to work fiine.

I find myself asking what's different about this time.  You said you were going to test your disks...  Was that a destructive test, in as much as all the data and maybe even the partitioning information would have been overwritten?  If so, when you previously tried other versions of Ubuntu that subsequently failed, did you start from a 'partition and create filesystem', or did the installation process allow you to skip that phase because it recognised that the disks had previously been set-up?

Personally, if I were doing a new installation, I would _always_ ensure that it starts out by partitioning and creating a filesystem from scratch.

Are you going to be brave enough to try 7.04 again?  If you do, make sure you blow away whatever was previously on the drive. You've had so many 'odd' things happen (no active swap partition, etc) that you need to be sure of starting from a clean base, otherwise you run the risk of having to deal with multiple problems.

If you do try 7.04 again and it fails in the same way, I'd urge you to look for further evidence as to what is causing the failure, rather than repeating what you've tried before and re-installing again.  You should be able to gather information about the boot and shutdown process from getting it to run verbosely and/or trawling through the various system logs in /var/log.

Mike

---

### Post by Ryoojin83 on 2007-08-05
Originally 6.10 worked fine, but after I wiped the drive (DBAN) I tried 7.04 and that was giving me the fail error.  then I DBANed it again and tried to go back to 6.10, where I was getting busy box.  It might have been because I had my 4 other drive hooked up too.

EDIT:  Either way its working now.  I honestly don't know what was wrong before.  The only thing a really changed was removing my four data drives, and installing those later.

Thanks everyone for your help!

---

### Post by toyz on 2007-08-09
> **Ryoojin83 said:**
> I guess I don't really see what is off the wall about using RAID 0 for swap.  
I have 2 partitions on each drive, the root partition (38GB) and swap partition (2GB), and the drives have to have identical root partitions in order to mirror.  so what do I do with the remaining 2 partitions?  I just wanted to make one big swap, with "better performance",  though I doubt it would since its pulling off of drives with another raided partition.   I guess I could just have made 2 swap spaces.  Didn't cross my mind at the time to make more than one though.

what do you recommend?  2 separate swap spaces?

YES!

Took me a while to find my source... From the Software RAID Howto:

> Q: How can I set up swap spaces using raid 0? Wouldn't striped swap ares over 4+ drives be really fast?

    A: Leonard N. Zubkoff replies: It is really fast, but you don't need to use MD to get striped swap. The kernel automatically stripes across equal priority swap spaces. 

---

### Post by aneas on 2007-09-27
I have a box setup with feisty server (2.6.20-16-generic x86_64). The following raid1 is setup using two 250 GB SATA drives (among other disks on the same system):
md0: /boot (sde1 + sdf1)
md1: swap (sde2 + sdf2)
md2: LVM [root, /home, etc] (sde3 + sdf3)

Everything is running as it expected, booting fine, mounting etc. However I have the same two issues described in this thread:

1. At startup:
mdadm: No devices listed in conf file were found.

This issue I dont care much about since all is working, I could possibly fix it with that sleep 10 thing.

2. At shutdown:
md1 and md2 fail to stop.

This issue is more serious to me. The fact that md0, which is not mounted before shutdown (nor containing swap or root) succeeds to stop is probably a clue to solving this. I have tried to only have the two system drives connected to the system, they then become sda and sdb but with the same issue.

Help appreciated!

---

### Post by aneas on 2007-09-30
bump, and perhaps this thread belongs in another forum?

---

