---
title: "Resize root partition using lvm?"
date: 2006-12-12
forum: General Help
---

### Post by EmmEff on 2006-12-12
I installed 6.06LTS on my server with an LVM root partition(/dev/mapper/Ubuntu-root), and now I wish to resize this partition.  What is the proper method?  Can I boot from a LVM-enabled rescue CD and resize?  Thanks in advance.

I am familiar with lvextend and resize2fs, however my recent experience on another machine destroyed the root partition when attempting to resize while mounted.

---

### Post by mlind on 2006-12-12
I've done using Ubuntu alternate cd (the one that uses old ncurses style installer). Any other distribution's livecd will probably do, it just need to contain lvm support on kernel, lvm tools and resize2fs or parted.
I've always used resize2fs to expand/shrink partition inside LV, but I recall Dapper's cd contains somewhat broken resize2fs. Use edgy's altenate cd if you get segmentation fault when resizing, that's what I did.

.. When you've booted using rescue cd,
[LIST] 
[*]if you expand a partition, first allocate new space using **lvextend**, then use resize2fs to that partition
[*]if you shrink a partition, first use resire2fs to shrink it, after that use **lvreduce**
[*]dont' use lvresize
[/LIST]

Here's how I would extend my root partition, which is /dev/VolGrp00/LVRoot
```

sudo lvextend -L +1GB /dev/VolGrp00/LVRoot
sudo resize2fs /dev/VolGrp00/LVRoot

```

resize2fs will probably prompt you to run fsck to expanded partition, so do it as it instructs and then run resize2fs again.

You can also use interactive shell that lvm offers. Type **help** inside the shell to see all available commands.
```

sudo lvm
#display information about volumes
vgs
lvs

```

---

### Post by EmmEff on 2006-12-13
Thanks.

lvresize let me resize the root filesystem while it was mounted. resize2fs wouldn't run while mounted, so the filesystem was put in a bad state.  When I booted from the live CD and attempted to run resize2fs, it choked (mismatch between reported filesystem size and partition size).  I now have to reinstall, but I'll be sure to try doing everything from the live CD as you describe.

---

### Post by mlind on 2006-12-13
Ouch! I guess you didn't read the warnings about resizing already mounted filesystems? I hope you didn't lost any unrecoverable data..

Don't resize mounted filesystems, and avoid using lvresize if you're not absolutely sure what you're doing. It will chunk off your data without any warnings. You should definitely boot using livecd now and force fsck on your root partition, its journal could be quite messed up.

I think you should also read [lvm HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO") before invoking any lvm or filesystem resizing commands.

---

### Post by EmmEff on 2006-12-13
I don't remember reading any warnings, but it was more of an experiment to see if it was possible :)

I'm not new to LVM (been running a software RAID5 array w/LVM for almost two years now), just new to having the root partition on LVM.

Nothing lost, aside from my time.  Thanks for the replies!

---

### Post by mlind on 2006-12-13
> **EmmEff said:**
> I don't remember reading any warnings, but it was more of an experiment to see if it was possible :)

I'm not new to LVM (been running a software RAID5 array w/LVM for almost two years now), just new to having the root partition on LVM.

Nothing lost, aside from my time.  Thanks for the replies!

Okay, that's good news then. Yeah, resizing root partition is problematic I recall. I had old Ubuntu install laying around on another LV, so I just rebooted and performed resizing the newer Ubuntu root there, without livecd.

---

### Post by EmmEff on 2006-12-14
Finally got things working properly last night.  Thanks for your help.

---

