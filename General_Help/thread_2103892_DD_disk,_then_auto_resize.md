---
title: "DD disk, then auto resize?"
date: 2013-01-11
forum: General Help
---

### Post by Roasted on 2013-01-11
Let's say I have a 160GB HDD in system A, and I want to DD that image to system B with 500GB. When I do this, system B's hard drive will come up as a 500GB drive with a 160GB partition, the rest remaining unallocated.

Is there a command I can run to help automate this process, where once DD is complete it effectively takes that partition and expands it to utilize the rest of the size of the hard drive? I'd like to stick to terminal if at all possible, as I know GParted would be a sweet option too.

---

### Post by tgalati4 on 2013-01-11
I always get shot down for this, but it works:

```
sudo cp /dev/sda /dev/sdb
```

This will take a while and it assumes that /dev/sdb is the new drive and much larger.

Then use gparted to add partitions or to expand the existing partition on the drive.

I've done this several times and it even works on WinXP partitions, resulting in bootable images.

You may have to make changes in GRUB to account for UUID changes of the drives, or just use /dev/sdX references in the boot menus.

---

### Post by Roasted on 2013-01-11
I'm not sure how I feel about using a simple cp command. dd makes more sense to me when I want the contents of drive A to be identical to drive B... I have a little project going on here where I'l be coming across a whole variety of systems, likely of different sized hard drives. My goal is to create a 10GB Ubuntu image and dd that to whatever drive is in the target system, whether it be a 40GB, 1TB, etc. The end goal is to have that 10GB image span across the entire disk. Isn't there a parted command or something that I missed?

---

### Post by dcstar on 2013-01-11
> **Roasted said:**
> Let's say I have a 160GB HDD in system A, and I want to DD that image to system B with 500GB. When I do this, system B's hard drive will come up as a 500GB drive with a 160GB partition, the rest remaining unallocated.

Is there a command I can run to help automate this process, where once DD is complete it effectively takes that partition and expands it to utilize the rest of the size of the hard drive? I'd like to stick to terminal if at all possible, as I know GParted would be a sweet option too.

Expanding partitions requires a specific tool for each filesystem type.

These tools are available but **you** will have to create a script to identify the correct tool and then launch it correctly to do the job.

---

### Post by Roasted on 2013-01-11
> **dcstar said:**
> Expanding partitions requires a specific tool for each filesystem type.

These tools are available but **you** will have to create a script to identify the correct tool and then launch it correctly to do the job.

Well, yeah. I kind of expected that. I was hoping for some sort of idea as to what specific commands would accomplish such a task.

---

### Post by sudodus on 2013-01-12
If you are doing it on a few computers, I would recommend gparted (you mentioned it in your first post).

If you are doing it on many computers, you cab buy HDDs of the same size. Then you can prepare one of them 'manually' to use the whole disk space, and afterwards you can clone it to mass produce identical systems.

Finally you might want to change the hostname to make them easier to identify in the network. (The mac address of the internet chip is unique, but anyway it's nice to have different hostnames.)

Another alternative is to use Remastersys and make an install iso file.

[[COLOR="Red"]http://www.remastersys.com/[/COLOR]]("http://www.remastersys.com/")

---

### Post by Roasted on 2013-01-12
> **sudodus said:**
> If you are doing it on a few computers, I would recommend gparted (you mentioned it in your first post).

If you are doing it on many computers, you cab buy HDDs of the same size. Then you can prepare one of them 'manually' to use the whole disk space, and afterwards you can clone it to mass produce identical systems.

Finally you might want to change the hostname to make them easier to identify in the network. (The mac address of the internet chip is unique, but anyway it's nice to have different hostnames.)

Another alternative is to use Remastersys and make an install iso file.

[[COLOR="Red"]http://www.remastersys.com/[/COLOR]]("http://www.remastersys.com/")

This isn't for computers on the same network... this idea is for re-purposing old systems on Ubuntu/LXDE for families that might be in financial hardships. As a result, even identical usernames wouldn't matter, which has its benefits since nothing needs to be renamed.

I had forgotten about remastersys. That sounds pretty good, I would just have to brew up an iso and go from there. GParted is undoubtedly a solid option too. I just thought for sure there was a terminal command to resize the partition.

---

### Post by sudodus on 2013-01-12
> **Roasted said:**
> This isn't for computers on the same network... this idea is for re-purposing old systems on Ubuntu/LXDE for families that might be in financial hardships. As a result, even identical usernames wouldn't matter, which has its benefits since nothing needs to be renamed.

I had forgotten about remastersys. That sounds pretty good, I would just have to brew up an iso and go from there. GParted is undoubtedly a solid option too. I just thought for sure there was a terminal command to resize the partition.

You have a good purpose and I think you know about suitable tools already.

If you watch gparted work, you will see the commands used, and you may identify them as linux commands.

If you want to learn more about terminal commands, browse the internet with a suitable search string, for example

[I]linux terminal command to resize partition
[/I]
By the way, you may need to do some individual tweaking anyway to run the graphics and/or wifi chip/card with proprietary drivers. This will be very different for different hardware, and often there is no need for proprietary drivers.

Good luck with your project :-)

---

